---
title: "&quot; TuningSignalCheck: SignalMonitor timed out&quot; errors in mythbackend log"
date: 2018-12-30
forum: Multimedia Software
---

### Post by Adam_Jacobs on 2018-12-30
I have noticed I am getting some error messages in my mythbackend log that look like this:

Dec 30 13:50:39 htpc mythbackend: mythbackend[926]: E TVRecEvent tv_rec.cpp:3933 (TuningSignalCheck) TVRec[5]: TuningSignalCheck: SignalMonitor timed out

As far as I know, everything is working OK, but it always makes me a little nervous if I see errors in the log file. Should I be worried about this?

I'm using MythTV 0.29 on Ubuntu 18.04

---

### Post by vidtek on 2018-12-30
> **Adam_Jacobs said:**
> I have noticed I am getting some error messages in my mythbackend log that look like this:

Dec 30 13:50:39 htpc mythbackend: mythbackend[926]: E TVRecEvent tv_rec.cpp:3933 (TuningSignalCheck) TVRec[5]: TuningSignalCheck: SignalMonitor timed out

As far as I know, everything is working OK, but it always makes me a little nervous if I see errors in the log file. Should I be worried about this?

I'm using MythTV 0.29 on Ubuntu 18.04

Adam-

If this is all you have to worry about, you must be very bored over the long holiday mate.
My back-end logs are chock-full of error messages, not got this one though!:o
I suspect it relates to tuner information derived from your local transmitter, they are perpetually shifting channels around in the digital era, it's probably a channel that used to be available from your local transmitter but is now defunct.:(

Cheers, Tony.

---

### Post by Adam_Jacobs on 2019-01-05
> **vidtek said:**
> Adam-

If this is all you have to worry about, you must be very bored over the long holiday mate.

Cheers, Tony.

Hah! If only! No, that was just one problem that I thought might be easy to solve. Plenty more where that came from!

---

