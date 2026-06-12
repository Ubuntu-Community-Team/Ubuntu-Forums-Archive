---
title: "Mythbuntu 10.04 acpi wake up problem"
date: 2011-04-12
forum: Multimedia Software
---

### Post by sam0th on 2011-04-12
hi there,

i´m configuring mythbuntu acpi wake up and got a problem:

i can tell the bios to wake up, and it works, but i dont know how to tell it to mythbuntu, i tried some howto´s i´ve found in the www but none of them seems to work for me, but i think the fault is sitting in front of the screen....
;)
[FONT=monospace]
[/FONT]sudo sh -c "echo `date '+%s' -d '+ 3 minutes'` > /sys/class/rtc/rtc0/wakealarm"

works well and the pc starts by itself three minutes later. the clock works in rtc-mode.

what doesn´t work is to tell mythbuntu to do so for recordings. i checked the commands in the console:

mythshutdown --shutdown

works well!

mythshutdown --setwakeup "2011-04-11 21:00:00"

gives no feedback and doesn´t seem to change anything.
i don´t know where the time should be written down in the database, maybe the time-format (sry i´m german :)) is wrong?
because when i do

sudo sh -c "/usr/bin/setwakeup.sh $time"

and then take a look to 

cat /proc/driver/rtc

nothing changed there.

i´m running mythfront and backend on the same pc and i´ve checked several command - settings in the mythbackend and at mythwelcome too, with no effort.

for some information my setwakeup.sh:

#!/bin/sh #$1 is the first argument to the script. It is the time in seconds since 1970 #this is defined in mythtv-setup with the time_t argument  echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm. echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm

i tried already several scripts for that, none worked so far.

and sudo visudo:

# User privilege specification root    ALL=(ALL) ALL  # Allow members of group sudo to execute any command after they have # provided their password # (Note that later entries override this, so you might need to move # it further down) %sudo ALL=(ALL) ALL # #includedir /etc/sudoers.d  # Members of the admin group may gain root privileges %admin ALL=(ALL) ALL %mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh
%sam0th ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh 
i think the commands to shutdown should work in the console too, or am i wrong?
whats wrong? i tried many post and threat found by google and i´m trying for three days now, i asked too in a german forum but i think there are only noobs or kiddy´s.

in my opinion i have a fault in the format of the time or one of the settings hast to be fault.

thanks for your time and help!

:confused:

---

### Post by sam0th on 2011-04-13
there is a file called timstamp at mythtv home.
should there be the next wakeup time? because the file wont change by my settings.
could it be a permission problem?

---

### Post by Blonddeeni on 2011-06-07
Gidday sam0th

I have had success with getting mythbuntu-8.10 to shutdown the computer and wake up when it wants by using the mythtv-setup (Mythbackend Setup from the Applications > System gui) to send the wakeup time straight to /sys/class/rtc/rtc0/wakealarm.

The backend setup screen I am referring to is:

General > Shutdown/Wakeup Options. About the third screen I think.

The settings that worked for me on 8.10 were:

Startup command:  I left this blank.
Block shutdown before client connected: I "unchecked" this
Idle shutdown timeout (secs): 120
Max wait for recordings (min): 31
Startup before rec. (secs): 300 (This gave my machine time to do any filesystem checks, which could take some time).
Wakeup time format : time_t
Command to set wakeup time: echo $time > /sys/class/rtc/rtc0/wakealarm
Server halt command: sudo shutdown -h now
Pre Shutdown check-command: sudo /usr/bin/MythShutdownCheck

The only "outside" script my machine used was my /usr/bin/MythShutdownCheck script, which I used to let the backend know whether it was ok to shutdown the machine.
(It wouldn't if any [or combination] of the following was true:
A frontend was running;
mythcommflag, &/or transcode was running.
A (dummy) user called jim was logged on).

I also edited the /etc/sudoers file and included mythtv as a user. I also included the /usr/bin/MythShutdownCheck and others in the final %mythtv line.

Also on boot, I had my /etc/rc.local file do the following:
sudo chown mythtv:mythtv /sys/class/rtc/rtc/wakealarm.

This made sure that mythtv could write to the file.

That made it all work for me on Mythbuntu-8.10.
The reason i am referring to Mythbuntu-8.10 is because the above did not work for me on Mythbuntu-11.04 which I have just had to install.
(I somehow got mythbackend / frontend out of setp with the "Database Schema" last week and it was all over for me. :( )

I am currently unable to write ANYTHING to /sys/class/rtc/rtc0/wakealarm, even as root.

I am not at my machine at the moment so cannot check anything else for you,but I hope that the above way of doing this, (writing the time straight from the backend to the wakealarm without going through another script), can give you some ideas on how to fix your problem.

Good luck. Time for me to keep looking for my fix. 
Cheers.
Blonddeeni.

PS: My system time used UTC, and in the bios for the motherboard did NOT "have wake on rtc alarm" enabled. It was disabled.

---

### Post by AKADAP on 2011-06-08
> **sam0th said:**
> 
mythshutdown --setwakeup "2011-04-11 21:00:00"
:confused:

First question: Are you trying to use mythwelcome?

mythshutdown is part of the mythwelcome program, and if you are not using mythwelcome, you should not be using it.

Second question: Have you read this wiki article? [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

I have mythTV working under Ubuntu with wakeup & automatic shut down using the setup listed under "Desktop Users" in the above wiki page.

---

### Post by sam0th on 2011-09-16
i´m sorry that i ignored your answers, i got it working two days later.
thanks for your hints, i think i read everything which google spit out, but the different solutions didin´t work for me.
also when i tryed them on a new stock system...

i will check your ideas in the future when i will upgrate my hardware and then software too.

the solution for me is this "setwakeup.sh":

> #!/bin/bash #$NEXTRECORDINGSEC is the time in seconds since 1970 NEXTRECORDING=`mysql -BN --database=mythconverg --user=xxxxx --password=xxxxx -e "select a.starttime from recordmatch a, record b where a.recordid = b.recordid and a.starttime >= now() $ #NEXTTIME has to be in time and date but from mysql comes date and time NEXTTIME=`echo $NEXTRECORDING | awk '{ print $2 " " $1 }'` #if NEXTTIME is nothing then NEXTRECORDINGSEC gets a time 5min in the past from now NEXTRECORDINGSEC=`date -d "${NEXTTIME} -2min" +%s` WEEKDAY=`date +%w` FACTOR=6 DAYSHIFT=`expr $FACTOR - $WEEKDAY` TODAY=`date +%D` TARGET=`date -d "09:55:00 ${TODAY} +${DAYSHIFT}day" +%s` NOW=`date +%s` echo "NEXTTIME = " $NEXTTIME echo "Now = " $NOW echo "Target = " $TARGET echo "Nextrecording = " $NEXTRECORDINGSEC if [ $NEXTRECORDINGSEC -gt $TARGET ] || [ $NEXTRECORDINGSEC -lt $NOW ]; then echo 0 > /sys/class/rtc/rtc0/wakealarm #this clears your alarm. echo $TARGET > /sys/class/rtc/rtc0/wakealarm #this writes your alarm fi  if [ $NEXTRECORDINGSEC -gt $NOW ] && [ $NEXTRECORDINGSEC -lt $TARGET ]; then echo 0 > /sys/class/rtc/rtc0/wakealarm #this clears your alarm. echo $NEXTRECORDINGSEC > /sys/class/rtc/rtc0/wakealarm #this writes your alarmnow i have to end manualy mythfrontend and then let shutdown the pc by mythwelcome using the script.
nicer would be to use the shutdown button from mythfrontend to execute the script, but till now it hadn´t worked.
like i said i have to try some other day in future for this solution.

i will check this threat from now on few times for some new i deas maybe.
thanks so far.

---

