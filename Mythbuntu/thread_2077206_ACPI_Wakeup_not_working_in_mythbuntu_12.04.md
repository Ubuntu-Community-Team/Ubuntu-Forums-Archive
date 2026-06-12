---
title: "ACPI Wakeup not working in mythbuntu 12.04"
date: 2012-10-28
forum: Mythbuntu
---

### Post by bigwoof on 2012-10-28
Hi there,

I have recently upgraded my backend to mythbuntu 12.04 but unfortunately I can not get AICP wakeup to work.

I followed this guide: 

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

and I can manually specify a shutdown time however the mythbackend process does not seem to set a wakeup time.

I have checked by running 

```
cat /proc/driver/rtc
```

and it comes up with no alarm set.

I have added the mythtv group to sudoers by adding the line

```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/setwakeup.sh
```

by running "sudo visudo"

Has anybody had similar issues, and do you know how to fix?

Cheers

Phil

---

### Post by Rotak on 2012-10-28
> 
and I can manually specify a shutdown time however the mythbackend process does not seem to set a wakeup time.
I am unsure what you mean by "manually specify SHUTDOWN time". So the first question is, whether the the console test of ACPI wake up worked (as described here: [http://www.mythtv.org/wiki/ACPI_Wakeup#Manually_test_wakealarm](http://www.mythtv.org/wiki/ACPI_Wakeup#Manually_test_wakealarm)).

There is another small question/checklist:


[LIST]
[*]Do you use UTC time for BIOS?
[*]Did you setup hwclock access?
[*]If you use UTC, did you make sure...
[LIST]
[*]you set UTCBIOS=true in setwakeup.sh?
[*]your bios clock is in UTC? ```
hwclock --systohc --utc
```
[/LIST]
 
[*]Does /usr/bin/setwakeup.sh have 755 rights (or higher)?
[*]Did you try this sudoers-line for testing: ```
%mythtv ALL=(ALL) NOPASSWD:ALL
```
[/LIST]
Hmm. I usually fail on one of these points, causing ACPI wake not to work on first try. ;)

---

### Post by bigwoof on 2012-10-28
Thanks Rotak

> **Rotak said:**
> [http://www.mythtv.org/wiki/ACPI_Wakeup#Manually_test_wakealarm](http://www.mythtv.org/wiki/ACPI_Wakeup#Manually_test_wakealarm)).

Yes I am able to get the machine to restart using the guide above.

I will run through the checklist tonight and let you know what comes up.

Thanks for the help.

Cheers

Phil

---

### Post by bigwoof on 2012-10-29
> **Rotak said:**
> 
[LIST]
[*]Do you use UTC time for BIOS?
[*]Did you setup hwclock access?
[*]If you use UTC, did you make sure...
[LIST]
[*]you set UTCBIOS=true in setwakeup.sh?
[*]your bios clock is in UTC? ```
hwclock --systohc --utc
```
[/LIST]
 
[*]Does /usr/bin/setwakeup.sh have 755 rights (or higher)?
[*]Did you try this sudoers-line for testing: ```
%mythtv ALL=(ALL) NOPASSWD:ALL
```
[/LIST]



I went through the list and all seems in order
[LIST]
[*]BIOS is set to UTC
[*]hwcloack asses is supressed
[*]added UTCBIOS=true to setwakeup.sh
[*]ran hwclock --systohc --utc
[*]setwakeup.sh has 755 rights
[*]added full sudo rights to mythtv group
[/LIST]

I also checked the mythtv settings in the backend set up

I will see what happens tonight 

Cheers

Phil

---

### Post by Rotak on 2012-10-29
One thing you can do for testing is to add this line at the end of your setwakeup.sh:

```
cat /proc/driver/rtc > /home/mythtv/lastrtc.txt
```Then you can see what was actually written into the BIOS before the system was shut down.

---

### Post by bigwoof on 2012-10-29
Thanks I will give it a shot but I have the feeling that it will not log as mythtv does not seem to be able to shut down the machine either.

I will also try adding some sort of logging string to the shutdown command to see if it is even initiated. 

It is as if mythtv can not achieve root privileges to set the rtc wake time and shut down them machine.  But I did add mythtv to the sudoers and checked the permissions on the setwakeup.sh script.

---

### Post by bigwoof on 2012-11-01
OK - It seems to be working properly now

I think it was a combination of not understanding how the recording system worked - I thought that the rtc wakeup was set when the backend ran mythfilldatabase so when I checked for an alarm it was not there - and I assumed it would not work.  

It looks like the backend goes through its shutdown procedure and that is when it checks for the next recording and sets the wake time just before it shuts down the machine.  

Thanks for the help 

At least now I have a better understanding of the backend processes.

---

### Post by nickrout on 2012-11-03
> **bigwoof said:**
> OK - It seems to be working properly now

I think it was a combination of not understanding how the recording system worked - I thought that the rtc wakeup was set when the backend ran mythfilldatabase I can see some logic in thinking that, but on deeper analysis, how would the backend know when the system was going to be shut down after it ran mythfilldatabase? The only time it knows when to wake up is at the time when it knows what time it is going to shut down.

---

### Post by bigwoof on 2012-11-03
Good Point.  At least it is working at now as long as I dont dreak anything :)

---

