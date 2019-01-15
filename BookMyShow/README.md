Function Requirements
- Our ticket booking service should be able to list down different cities where its affiliate cinemas are located.
- Once the user selects the city, the service should display the movies released in that particular city.
- Once the user selects the movie, the service should display the cinemas running that movie and its available shows.
- The user should be able to select the show at a particular cinema and book their tickets.
- The service should be able to show the user the seating arrangement of the cinema hall. The user should be able to select multiple seats according to their preference.
- The user should be able to distinguish available seats from the booked ones.
- __Users should be able to put a hold on the seats for five minutes before they make a payment to finalize the booking.__
- The user should be able to wait if there is a chance that seats might become available – e.g. when holds by other users expire.
- Waiting customers should be serviced fairly in a first come first serve manner.


Non-Functional Requirements:
- The system would need to be highly concurrent. There will be multiple booking requests for the same seat at any particular point in time. The service should handle this gracefully and fairly.
- The core thing of the service is ticket booking which means financial transactions. This means that the system should be secure and the database ACID compliant.


Some design consideration
- For simplicity, let’s assume our service doesn’t require user authentication.
- The system will not handle partial ticket orders. Either user gets all the tickets they want, or they get nothing.
- Fairness is mandatory for the system.
- To stop system abuse, we can restrict users not to book more than ten seats.
- We can assume that traffic would spike on popular/much-awaited movie releases, and the seats fill up pretty fast. The system should be scalable, highly available to cope up with the surge in traffic.


4. Capacity Estimation
Traffic estimates: Let’s assume that our service has 3 billion page views per month and sells 10 million tickets a month.

Storage estimates: Let’s assume that we have 500 cities and on average each city has ten cinemas. If there are 2000 seats in each cinema and on average, there are two shows every day.

Let’s assume each seat booking needs 50 bytes (IDs, NumberOfSeats, ShowID, MovieID, SeatNumbers, SeatStatus, Timestamp, etc.) to store in the database. We would also need to store information about movies and cinemas, let’s assume it’ll take 50 bytes. So, to store all the data about all shows of all cinemas of all cities for a day:





