---
title: "Network Usage Accounting Program?"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by Sad_Panda on 2010-06-10
I'm looking for a program to monitor my network connection and let me know how much data I've downloaded this "month".

I live in a rural area, and either satellite or cellular internet connection are the only options. I currently have a cellular internet connection through Verizon. In either case, there is a monthly quota on data transfer. After this quota is reached, the internet service provider either severely clamps down on your transfer rate (WildBlue satellite) or starts charging some number of cents per megabyte (Verizon).

In either case, it would be super awesome to have a program that you could set up with things like the quota amount, interface to monitor, and the billing period, which would then monitor that interface and return the amount of the quota that has been used, either in percent of total quota or in plain megabytes. Or possibly, there could be two numbers, percent of "month" remaining, followed by percent of quota remaining. It would be particularly awesome if this were an applet.

Of course, the exact program I want probably doesn't exist, but I'm having trouble finding anything at all that is similar. The important thing is that it has to maintain the total amount of data transfer through a reboot, which the system monitor doesn't do (for example).

I'm a bit surprised that I can't find anything because I would have guessed that dial-up users would need this functionality. I'm using the normal Ubuntu network connection applet to operate a USB 760 cellular modem. I have not been able to get Verizon's VZAccess program to work. It does, I believe, have usage reporting functionality. However, even if I could get it to work, it does not provide real-time data and is rather awkward to use.

---

### Post by iponeverything on 2010-06-11
don't be sad panda!

There is program vnstat that you install via apt. I am in same boat as you where I have quota that don't want exceeded. 

I have 3G and I am able to query my quota status via an AT modem command. So just wrote a small script to does the query once and hour and prints out my status. I have a 5 gig quota, and output of my script looks like so:

Fri Jun 11 12:01:01 TJT 2010
Cap:5000 Current:4149.85 Used:850.15
Rate Average: 77 Mb/day
The Average Left for the Month is 207 Mb/day

If you have a way to query you quota status, I can post my script and you can modify it for your use..

fyi that is the output from vnstat daily use query:

```
ppp0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   15.05.    228.28 MB  |   27.25 MB  |  255.53 MB   %%%%%%%:
   16.05.    169.55 MB  |   13.91 MB  |  183.45 MB   %%%%%
   17.05.     71.92 MB  |   19.78 MB  |   91.70 MB   %%
   18.05.    150.76 MB  |   16.98 MB  |  167.74 MB   %%%%:
   19.05.     93.70 MB  |    9.30 MB  |  103.00 MB   %%%
   20.05.    111.40 MB  |   23.10 MB  |  134.50 MB   %%%:
   21.05.    101.80 MB  |   12.47 MB  |  114.27 MB   %%%
   22.05.     66.08 MB  |    8.04 MB  |   74.11 MB   %%
   23.05.     69.17 MB  |    9.76 MB  |   78.93 MB   %%
   24.05.    154.67 MB  |   15.42 MB  |  170.09 MB   %%%%%
   25.05.     83.86 MB  |    7.43 MB  |   91.29 MB   %%
   26.05.    120.57 MB  |   11.60 MB  |  132.17 MB   %%%%
   27.05.     40.96 MB  |    5.82 MB  |   46.79 MB   %
   28.05.       367 kB  |     156 kB  |     523 kB
   27.05.     59.83 MB  |    8.27 MB  |   68.10 MB   %%
   28.05.     56.03 MB  |    7.01 MB  |   63.04 MB   %%
   29.05.    220.07 MB  |   12.85 MB  |  232.92 MB   %%%%%%%
   30.05.     35.86 MB  |    5.33 MB  |   41.19 MB   %
   31.05.    750.46 MB  |   22.31 MB  |  772.77 MB   %%%%%%%%%%%%%%%%%%%%%%%%:
   01.06.     14.99 MB  |    5.28 MB  |   20.27 MB
   02.06.     53.19 MB  |    5.63 MB  |   58.82 MB   %
   03.06.     55.37 MB  |    7.79 MB  |   63.16 MB   %%
   04.06.     41.00 MB  |    6.21 MB  |   47.20 MB   %
   05.06.     81.63 MB  |    7.13 MB  |   88.76 MB   %%
   06.06.     92.83 MB  |    9.58 MB  |  102.41 MB   %%%
   07.06.     84.18 MB  |    9.86 MB  |   94.04 MB   %%%
   08.06.     68.36 MB  |    7.12 MB  |   75.48 MB   %%
   09.06.    204.92 MB  |   16.87 MB  |  221.79 MB   %%%%%%:
   10.06.    361.29 MB  |   36.50 MB  |  397.79 MB   %%%%%%%%%%%:
   11.06.      7.37 MB  |    2.26 MB  |    9.63 MB


```

---

### Post by Sad_Panda on 2010-06-11
That sounds promising. 

I would like to see your script. I bet there's a way to query the quota status, and it's probably the same method you're able to use.

Thanks!

---

### Post by iponeverything on 2010-06-12
Install both cu and expect through apt.

ok there are a few pieces to the puzzle. The first piece is script that using scripting language called expect that calls called cu to query the modem. My expect script is named "exp" and is as follows:

root@gateway:/etc# cat /usr/local/bin/exp
```

#!/usr/bin/expect --


set command1 "AT+CUSD=1,\"#2001#2#\",15"
set command2 "AT"

spawn cu -l /dev/ttyUSB1
expect "Connected."

sleep 3

send "AT\r"
expect "OK"

send "$command1\r"
expect "OK"

expect CUSD
exit

```

exp is called by bash script called grab parses the results from exp, does the math and gives me something I can use, and it as follows:

```

#!/bin/bash
sudo chown uucp /dev/ttyUSB1

eval `date "+dim_m=%m dim_y=%Y"`

_DAYS_IN_MONTH=`cal $dim_m $dim_y | egrep -v '[A-Za-z]' | wc -w`

_DATE_TODAY=`date +%d`

let SUBTRACTION1=`echo $_DAYS_IN_MONTH-$_DATE_TODAY |bc`
let SUBTRACTION=`echo $SUBTRACTION1+1|bc`

sudo /usr/local/bin/exp|grep Mb\
|awk 'T = 5000-$10 {print "Cap:5000 Current:"$10" Used:"T}' \
|tee /tmp/ffile |awk -F\: '{print " echo "$4" / `date +%d` | bc "}'\
|sh|awk '{print "echo `cat /tmp/ffile` ; echo Rate Average: "$1" Mb/day"}' |sh

_LEFT=`cat /tmp/ffile |awk -F\: '{print $3}'|awk '{print $1}'`

AVER=`echo $_LEFT/$SUBTRACTION |bc`

echo The Average Left for the Month is $AVER Mb/day

```

Grab is called by cronjob once every hour and puts the results on a webpage.

---

