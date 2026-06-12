---
title: "Some DVD titles fail."
date: 2008-12-15
forum: Mythbuntu
---

### Post by PhilWig on 2008-12-15
I'm a newbie to Mythbuntu (8.04) and Linux in general.
If I try to play DVDs some work, others don't.  eg

Sunday Times freebee about freak weather - okay
Angela Ripon ballroom dancing - fine
Mama Mia, 24 Series 5,   - a blank screen, disk spinup, then reverts to videos menu.
Dead Poets Society - fails similarly after selecting the language (English/Spanish).

There are kernel messages in /var/log/messages
{but I've left pruned them}

: [ 4420.155715] end_request: I/O error, dev sr0, sector 545912
: [ 4420.155724] printk: 3 messages suppressed.
: [ 4420.352568] end_request: I/O error, dev sr0, sector 546040
: [ 4422.482552] UDF-fs: Partition marked readonly; forcing readonly mount
: [ 4422.482566] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MAMMA_MIA', timestamp 2008/09/26 20:18 (1000)
: [ 4424.001289] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.116186] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.231066] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.414782] end_request: I/O error, dev sr0, sector 14945348

If I run Xine it rejects the same titles at the same places with the error messages:
The source can't be read.  Maybe you don't have enough rights for this or source doesn't contain data (eg: not disk in drive). This is followed by:
(Error reading from DVD.)  or (Error reading NAV packet)

The common factor with the DVDs which will not play seem to be that they are all commercial titles and are Dolby and region 2.  All have been properly and legitimately sourced in the UK.

All titles play fine on the same computer if I swap boot disk and run under XP, and they are fine on the sitting room DVD player.

Any clues please?

A subsidiary question:  I understand that DVD drives have a region code which can only be set a limited number of times before the device locks up.  Will I be using up these 'drive lives' by re-installing or re-booting back and forth between XP and Ubuntu?

Thanks
Phil

---

### Post by alwayshere on 2008-12-15
try using vlc player it will play almost anything

---

### Post by larsolav on 2008-12-15
Did you enable DeCSS in the mythbuntu control center?

---

### Post by PhilWig on 2008-12-15
Isn't that typical!   Struggle for a week, post a pleading message then twig how to fix it almost immediately.
Applications > System > Myth control centre > proprietary codecs > install Medibuntu codecs

Thank you Medibuntu.
Phil

---

### Post by klc5555 on 2008-12-15
> **PhilWig said:**
> I'm a newbie to Mythbuntu (8.04) and Linux in general.
If I try to play DVDs some work, others don't.  eg

Sunday Times freebee about freak weather - okay
Angela Ripon ballroom dancing - fine
Mama Mia, 24 Series 5,   - a blank screen, disk spinup, then reverts to videos menu.
Dead Poets Society - fails similarly after selecting the language (English/Spanish).

There are kernel messages in /var/log/messages
{but I've left pruned them}

: [ 4420.155715] end_request: I/O error, dev sr0, sector 545912
: [ 4420.155724] printk: 3 messages suppressed.
: [ 4420.352568] end_request: I/O error, dev sr0, sector 546040
: [ 4422.482552] UDF-fs: Partition marked readonly; forcing readonly mount
: [ 4422.482566] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MAMMA_MIA', timestamp 2008/09/26 20:18 (1000)
: [ 4424.001289] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.116186] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.231066] end_request: I/O error, dev sr0, sector 14945344
: [ 4424.414782] end_request: I/O error, dev sr0, sector 14945348

If I run Xine it rejects the same titles at the same places with the error messages:
The source can't be read.  Maybe you don't have enough rights for this or source doesn't contain data (eg: not disk in drive). This is followed by:
(Error reading from DVD.)  or (Error reading NAV packet)

The common factor with the DVDs which will not play seem to be that they are all commercial titles and are Dolby and region 2.  All have been properly and legitimately sourced in the UK.

All titles play fine on the same computer if I swap boot disk and run under XP, and they are fine on the sitting room DVD player.

Any clues please?

A subsidiary question:  I understand that DVD drives have a region code which can only be set a limited number of times before the device locks up.  Will I be using up these 'drive lives' by re-installing or re-booting back and forth between XP and Ubuntu?

Thanks
Phil

I confess I gave up on Mythtv as a prerecorded DVD-player a long time ago. Just too frustratingly hit-or-miss to be worthwhile, even with Region 1 DVDs, for the various playback errors you've mentioned, and several others besides. In addition to frequent stuttering, jerkiness, and buffering pauses (depending on the DVD). A serious negative influence on the WAF. 

For prerecorded DVD playback, I settled on using a cheapie regionless dedicated DVD player that pipes into the composite input of an old PVR-150 analog card and into Mythtv that way. (I don't own an actual television to connect the dedicated DVD player to.) 

I set up a separate input for the player "External DVD player" in the backend, so that I can switch to "External DVD player" as an input menu option while watching Live TV. I just avoid scheduling analog recordings on that tuner during likely DVD-watching hours (i.e. evenings and weekends) and live with the fact that any DVD-player remote command will take between 4 and 20 seconds to appear to execute because of Myth buffering the PVR-150 output. 

But no crashes, no playback peculiarities, ergo much higher WAF.

Cheers!

---

### Post by jboehm on 2008-12-16
FYI: there is a current bug in DVD playback.  Myth will freeze on still frames.  So the first FBI warning you hit ... crash.  Example titles that I know of are Cars and Pirates I.

---

### Post by mike909 on 2009-02-24
> **jboehm said:**
> FYI: there is a current bug in DVD playback.  Myth will freeze on still frames.  So the first FBI warning you hit ... crash.  Example titles that I know of are Cars and Pirates I.

Jboehm,
Could you please post a link to that bug? I believe I am hitting it with Tarzan DVD and want to track it. Thanks.

---

### Post by tehbeermang on 2009-02-25
Problem movies I have run across:

Wall E:

If I select "play movie" it flip flops between the FBI warning and the commentary disclaimer.

If I go into chapter selection and select chapter 1, it plays fine.

Haven't found the title that rips the full movie.

Same with Finding Nemo, except I can rip if I choose Finding_Nemo title 1.

Kung Fu Panda: forget it. Blank screen all the way around.

Saw III: locks up on the Lionsgate logo.

---

### Post by pulpinator on 2009-05-10
> **tehbeermang said:**
> Problem movies I have run across:

Wall E:

If I select "play movie" it flip flops between the FBI warning and the commentary disclaimer.

If I go into chapter selection and select chapter 1, it plays fine.

Haven't found the title that rips the full movie.


Title 30 worked for me. From here:

[http://ubuntuforums.org/showthread.php?p=7251761](http://ubuntuforums.org/showthread.php?p=7251761)

---

