---
title: "No program data exists"
date: 2014-01-05
forum: Mythbuntu
---

### Post by 7i2q on 2014-01-05
Hey, I'm trying to use the Remove Commercials script from the MythTV wiki, but this is not a problem with that script. 

Whenever I run mythcommflag or mythutils from the command line using the "chanid" and "starttime" parameters, I get:

```

2014-01-05 17:14:18.451621 E  No program data exists for channel 1779 at 20131129220300

```

I can bypass the problem for mythcommflag by using the file name instead of chanid and starttime, but mythutil doesn't have that option. 

I'm using a userjob to put the chanid and starttime into a text file so I can copy and paste them, so I know that they are correct. It happens with every recording I've tried. Commercial flagging works just fine with the file name, but when I try to use mythutils to "gencutlist", I get the error.

Does anyone know how to solve this?

---

### Post by 7i2q on 2014-01-06
I found a solution. Part of the problem is that mythutil wants the time in UTC, so you have to use %STARTTIMEUTC% in the user job. The job was still failing though, so I started stripping the script down to just the parts that actually do work. (there are is a lot of error checking) After that, it started working perfectly. I don't know why it worked, all I know is that it did.

I hope I've helped someone else with a similar problem.

---

