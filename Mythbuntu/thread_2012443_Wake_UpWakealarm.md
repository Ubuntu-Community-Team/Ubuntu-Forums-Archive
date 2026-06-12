---
title: "Wake Up/Wakealarm"
date: 2012-06-29
forum: Mythbuntu
---

### Post by K9KungFu on 2012-06-29
Hi,

I have followed these instructions [http://ubuntuforums.org/archive/index.php/t-1370585.html](http://ubuntuforums.org/archive/index.php/t-1370585.html) to the letter without any errors but my PC will not wake up!  My PC supports RTC and I have upgraded my BIOS and am on the latest mythbuntu release.  Any help will be gratefully received!

---

### Post by Lester_Burnham on 2012-06-29
Hi,

Is rtc wake enabled or disabled in the BIOS. Mine have always been disabled to work.
I use the method documented below on systems including 12.04 so far.
[http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__wake__fromsearch__1#entry246206](http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__wake__fromsearch__1#entry246206)

If the first stage works, everything else should work.

Lester

---

### Post by K9KungFu on 2012-06-29
> **Lester_Burnham said:**
> Hi,

Is rtc wake enabled or disabled in the BIOS. Mine have always been disabled to work.
I use the method documented below on systems including 12.04 so far.
[http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__wake__fromsearch__1#entry246206](http://www.pcmediacenter.com.au/forum/topic/35208-acpi-wake-mythbuntu-810-rtc/page__p__246206__hl__wake__fromsearch__1#entry246206)

If the first stage works, everything else should work.

Lester

I have a Dell 760, in the BIOS I have the alarm disabled but cannot find any RTC option although on Dell's website it states that it supports it.  Also the Wakealarm file is blank, I take it that's meant to be as it writes the alarm settings each time then clears?

---

### Post by Lester_Burnham on 2012-06-29
> **K9KungFu said:**
> I have a Dell 760, in the BIOS I have the alarm disabled but cannot find any RTC option although on Dell's website it states that it supports it.  Also the Wakealarm file is blank, I take it that's meant to be as it writes the alarm settings each time then clears?

Hi,

I had a quick read up on the dell 760 bios. It says there is an A02 bos to "Enhanced RTC wakeup capability" :)
[http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=KKFVV&fileId=2731118833](http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=KKFVV&fileId=2731118833)

I think there is only one machine I've tried that would not wake at all and that was a HP dc7700, so good luck is all I can say. Sorry. Can't beat building you're own when it comes to this type of thing.

Lester

---

### Post by K9KungFu on 2012-06-29
> **Lester_Burnham said:**
> Hi,

I had a quick read up on the dell 760 bios. It says there is an A02 bos to "Enhanced RTC wakeup capability" :)
[http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=KKFVV&fileId=2731118833](http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=KKFVV&fileId=2731118833)

I think there is only one machine I've tried that would not wake at all and that was a HP dc7700, so good luck is all I can say. Sorry. Can't beat building you're own when it comes to this type of thing.

Lester

It states that for the later BIOS I have (A13) I think this is a lost cause which is a shame as everything else works perfectly!  Ive got another PC laying about somewhere so I will give that a go.

Your help is appreciated!

All the best
J

---

### Post by alien878 on 2012-06-30
Did it wake up with a manual test?  If it did and your problem is using the scripts, it might be a permissions issue.  You can echo debug info to a log file in the set_wakeup script to maybe figure out what is going on.

Another thing to try:  The HWCLOCK changes in that document are out of date.  At least, I no longer need to make those changes.  You might try without them.

---

### Post by jim09 on 2012-07-08
Just noted that when I upgraded from 10.10 to 12.04, I had to make changes to /etc/sudoers as the format was slightly different.  It is best to test the commands as the myth user and make sure they run properly.  I also had to revert to the older nvram-wakeup.:(

---

### Post by mymythtv on 2012-07-09
Hi

I upgraded from 10.04/0.24 to 12.04/0.25. After that I couldn't turn on htpc with remote control anymore ( and still can't ). I don't do suspend/resume, but full shutdown ( power off )

Also when shutting down, it sometimes hang in "K51lirc" - havn't figured out yet why, but it might have something to do with my generel problem..

Looking high and low, I found out that other than I have problem with 3.2 kernel regarding suspend/resume/wakeup (google "kernel 3.2 wakeup" )

Power on by keyboard still works ( PS2 keyboard, not USB ), but USB wakeup dosn't work.

Booting on kernel 2.6.32-41, performing a "shutdown" made it possible to turn on by remote control again, so problem is not hardware, but related to kernel.

Next in plan is going for 3.3 kernel to see if problem persist, but that's another thread ( not hijacking this one :-)  )

/Bjarne

---

