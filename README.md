# Constants for Time Calculations

```javascript
const MILLISECONDS_PER_SECOND = 1000;
const SECONDS_PER_MINUTE = 60;
const MINUTES_PER_HOUR = 60;
const HOURS_PER_DAY = 24;
const DAYS_PER_YEAR = 365.25; // Average, accounting for leap years
```

# Working with Dates

**Current Date and Time**
```javascript
const now = new Date();
```

**Creating a Specific Date**
```javascript
const specificDate = new Date(2023, 0, 1); // January 1, 2023
```

**Extracting Date Components**
```javascript
const year = now.getFullYear();
const month = now.getMonth(); // 0-indexed (0 = January, 1 = February, ...)
const day = now.getDate();
const hour = now.getHours();
const minute = now.getMinutes();
const second = now.getSeconds();
```

# Formatting Dates

**Converting to a String**
```javascript
const dateString = now.toString();
```

**Formatting as YYYY-MM-DD**
```javascript
const formattedDate = `${now.getFullYear()}-${now.getMonth() + 1}-${now.getDate()}`;
```

**Locale-Specific Formats**
```javascript
const localeDate = now.toLocaleDateString('en-US'); // 'MM/DD/YYYY' for US
```

# Calculating Differences Between Dates

**Difference in Milliseconds**
```javascript
const date1 = new Date(2023, 0, 1);
const date2 = new Date(2023, 1, 1);
const differenceInMilliseconds = date2 - date1;
```

**Difference in Seconds**
```javascript
const date1 = new Date(2023, 0, 1);
const date2 = new Date(2023, 1, 1);
const differenceInMilliseconds = date2 - date1;
const differenceInSeconds = differenceInMilliseconds / MILLISECONDS_PER_SECOND;
```

**Difference in Days**
```javascript
const differenceInDays = Math.ceil(differenceInMilliseconds / (MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR * HOURS_PER_DAY));
```

**Difference in Years, Months, Days**
```javascript
const years = date2.getFullYear() - date1.getFullYear();
const months = date2.getMonth() - date1.getMonth();
const days = date2.getDate() - date1.getDate();
```

# Explanation of the Constant Calculation

The expression `MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR * HOURS_PER_DAY` is used to calculate the total number of milliseconds in a day. Here's the breakdown:

- **MILLISECONDS_PER_SECOND**: There are 1000 milliseconds in a second.
- **SECONDS_PER_MINUTE**: There are 60 seconds in a minute.
- **MINUTES_PER_HOUR**: There are 60 minutes in an hour.
- **HOURS_PER_DAY**: There are 24 hours in a day.

So, when you multiply these values together:

- First, `SECONDS_PER_MINUTE * MINUTES_PER_HOUR` calculates the number of seconds in an hour (60 seconds/minute * 60 minutes/hour = 3600 seconds/hour).
- Next, multiplying by `HOURS_PER_DAY` gives the total number of seconds in a day (3600 seconds/hour * 24 hours/day = 86400 seconds/day).
- Finally, multiplying by `MILLISECONDS_PER_SECOND` converts this to milliseconds (86400 seconds/day * 1000 milliseconds/second).

**Complete Calculation:**
```javascript
const MILLISECONDS_PER_DAY = MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR * HOURS_PER_DAY; // 86400000
```

# Using Math

**Rounding Numbers**
```javascript
const roundedDown = Math.floor(5.95);
const roundedUp = Math.ceil(5.05);
const rounded = Math.round(5.5);
```

**Random Numbers**
```javascript
const randomNum = Math.random();
```

**Finding Maximum and Minimum**
```javascript
const maxNum = Math.max(1, 3, 5);
const minNum = Math.min(1, 3, 5);
```

# Math and Dates

**Getting UNIX Timestamp (Seconds Since Epoch)**
```javascript
const unixTimestamp = Math.floor(Date.now() / MILLISECONDS_PER_SECOND);
```

**Converting UNIX Timestamp to Date**
```javascript
const dateFromUnix = new Date(unixTimestamp * MILLISECONDS_PER_SECOND);
```

**Rounding to Nearest Hour**
```javascript
const nearestHour = new Date(Math.round(now.getTime() / (MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR)) * (MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR));
```

**Calculating Age from Birthdate**
```javascript
const birthdate = new Date(1990, 0, 1);
const age = Math.floor((now - birthdate) / (MILLISECONDS_PER_SECOND * SECONDS_PER_MINUTE * MINUTES_PER_HOUR * HOURS_PER_DAY * DAYS_PER_YEAR));
```
