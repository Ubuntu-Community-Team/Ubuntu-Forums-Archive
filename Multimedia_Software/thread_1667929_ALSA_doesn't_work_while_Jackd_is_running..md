---
title: "ALSA doesn't work while Jackd is running."
date: 2011-01-15
forum: Multimedia Software
---

### Post by Buttons840 on 2011-01-15
I'm able to start jackd from the shell and also using qjackdctl.  In order to start jackd there must be no other applications "using" sound.  If I try to start jackd while watching a youtube video for example, I will receive an error saying that HW:0 can't be acquired.

What I'm trying to do is record an internet radio stream.  I can listen to the steam ok while jackd is not running.  If jackd is running, I cannot hear the stream, however the stream begins working the same second that I stop jackd.

Is this normal?  I'm not really sure how jackd is suppose to work.  If there are any tutorials I can read about jackd or other sound applications like alsa they would be helpful.

Thanks.

---

### Post by BicyclerBoy on 2011-01-15
Alsa & Jack are planned to work better together in future.

AFAIK now jack does not share the audio devices.

Jack is not just another sound application, it is a complete real-time audio subsystem intended for use with collection of other apps & instruments like Rosegarden fluidsyth midi devices etc.

I doubt you have any need for Jack.

Pulse audio & alsa can most likely achieve what 99% of what people require.

You likely need the gnome-alsa-mixer or pulse audio mixer & sound recorder.

---

### Post by lidex on 2011-01-16
> **Buttons840 said:**
> I'm able to start jackd from the shell and also using qjackdctl.  In order to start jackd there must be no other applications "using" sound.  If I try to start jackd while watching a youtube video for example, I will receive an error saying that HW:0 can't be acquired.

What I'm trying to do is record an internet radio stream.  I can listen to the steam ok while jackd is not running.  If jackd is running, I cannot hear the stream, however the stream begins working the same second that I stop jackd.

Is this normal?  I'm not really sure how jackd is suppose to work.  If there are any tutorials I can read about jackd or other sound applications like alsa they would be helpful.

Thanks.

If you just want to record streaming audio have a look here:
[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

