---
title: "ACPI wakeup not working Mythbuntu 12.04"
date: 2014-03-09
forum: Mythbuntu
---

### Post by waynelivingstone on 2014-03-09
I am trying to set up Mythbuntu to wake and sleep automatically with MythWelcome. 

I already have this working perfectly with my existing setup of MythDora 12 (based on Fedora 12). I am using all the same hardware and just swapping the hard drive out for the Mythbuntu install. 

I have been following this guide but am stuck on Manually test wakealarm:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

When I run the test commands: 
> 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm

cat /proc/driver/rtc

I get this: 

rtc_time        : 05:31:47
rtc_date        : 2014-03-09
alrm_time       : 05:36:43
alrm_date       : 2014-03-09
alarm_IRQ       : yes
alrm_pending    : no
update IRQ enabled      : no
periodic IRQ enabled    : no
periodic IRQ frequency  : 1024
max user IRQ frequency  : 64
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
BCD             : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay


That looks correct to me but when I shutdown it doesn't start up again. I have tried everything I can think of to get it to work. 

I suspect that the problem could be with the need to disable hwclock updates. The guide says to edit /etc/init/hwclock-save.conf like this: 
> 
# hwclock-save - save system clock to hardware clock
# hwclock-save - save system clock to hardware clock
#
# This task saves the time from the system clock back to the hardware
# clock on shutdown.

description    "save system clock to hardware clock"

start on runlevel [06]

task

script[INDENT]. /etc/default/rcS[/INDENT]
[INDENT][ "$UTC" = "yes" ] && tz="--utc" || tz="--localtime"[/INDENT]
[INDENT][ "$BADYEAR" = "yes" ] && badyear="--badyear"[/INDENT]
[INDENT]ACPITIME=`cat /proc/acpi/alarm`[/INDENT]
[INDENT]exec hwclock --rtc=/dev/rtc0 --systohc $tz --noadjfile $badyear[/INDENT]
[INDENT]echo "$ACPITIME" > /proc/acpi/alarm[/INDENT]
 end script

But /proc/acpi/alarm does not exist anymore it seems. 

I cant find any information for what I should do from here. Can anybody help me please?

---

### Post by Lester_Burnham on 2014-03-13
Hi,

I still use the old method I used on 8.10
I think I've tested it on 12.04

[http://lester-burnham.id.au/acpi-wake-mythbuntu-8-10/](http://lester-burnham.id.au/acpi-wake-mythbuntu-8-10/)

Lester

---

### Post by alien878 on 2014-03-13
> **waynelivingstone said:**
> I suspect that the problem could be with the need to disable hwclock updates. The guide says to edit /etc/init/hwclock-save.conf like this: 


But /proc/acpi/alarm does not exist anymore it seems. 

I cant find any information for what I should do from here. Can anybody help me please?
Hmmm.... I thought the hwclock problems had been resolved some time ago.

Anyway, you can probably test it by changing /proc/acpi/alarm to /sys/class/rtc/rtc0/wakealarm

---

