---
title: "channel discovery"
date: 2008-09-21
forum: Mythbuntu
---

### Post by whitty on 2008-09-21
Ok, i'm in Boston, MA, USA. I am attempting to install mythbuntu on an older gateway laptop, but nothing too slow to handle it (or shouldn't be) - athlon 64 4000+ radeon mobility x600, 1gb ram... I'm trying to use the Elgato EyeTV Hybrid, AKA WinTV HVR-950q as a capture card (usb external). I have an account with schedules direct, and after much effort for seemingly no reason, I FINALLY have gotten myth backend to log into that account and recognize my listing. now the problem is simply that i cant get channels imported. "Fetch channels from listings source" simply doesn't work, and when I try to scan for channels, every combination of settings results in a bunch of failures to tune channels, and eventually, if left to run long enough, the scan locks itself up. This is odd since this particular cable lineup should be 98% standard, analog cable, and there should be two or 3, maybe 5 ClearQAM channels, maybe 2-3 HD.

All I want to do is watch tv on this old laptop and make it useful as a PVR, but I've spent probably two months on and off trying to get this damn thing to work! Any ideas? I'm losing my mind.

Alex

---

### Post by Eric Boring on 2008-09-21
Well, I'll ask this because it's the first thing to check:

Do you have an antenna plugged into the tuner card? 

Failing that, it looks like there are some instructions for this card here : [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950).

Hope that helps.

---

### Post by whitty on 2008-09-23
As a matter of fact, I don't. Which makes the situation worse - it's cable. Both standard analog and clear QAM. If it were antenna, ATSC is pretty straightforward.

---

### Post by Eric Boring on 2008-09-24
> **whitty said:**
> As a matter of fact, I don't. Which makes the situation worse - it's cable. Both standard analog and clear QAM. If it were antenna, ATSC is pretty straightforward.

OK, but there's something plugged into the card right?:) Are you sure that the cable box is sending a signal? Can you view the output on your TV without running it through the Myth Machine? 

If it's indeed sending a signal, you could try logging into MythWeb and entering them by hand. (Settings > TV > Channel Info). I had to do that with my OTA set-top box, since it naturally only sent one channel unless I changed the channel. Come to think of it, are you using a set-top box for this? Maybe you could start the auto detect process and the flip through the channels as it scans for each?

---

### Post by whitty on 2008-09-24
Nope, I'm in college - just one big multiplex being sent down the line. Yes, I know the line works, my roommate has an actual tv (of course, no recording) and, in fact, I know the card works because it's actually an ElGato EyeTV Hybrid for the Mac - the hardware is physically the same as an HVR-950Q, but it comes with wonderful mac software that is just gorgeous and works perfectly. So in fact, I know the card is perfectly capable of tuning all the channels here. I usually use the mac, in fact, but I want to make this other laptop a mythtv machine specifically so that I can leave it at home all the time to record things when I'm away.

Alex

---

### Post by Eric Boring on 2008-09-24
Dang. I think I'm out of my league on this one then. Hopefully someone else can help you out. 
Good Luck. 
-Josh

---

### Post by newlinux on 2008-09-24
Maybe the card isn't configured right in your system. Can you use the card outside of myth in Linux on your system?

Also, if you tell us how you setup the card (what steps you took to install it and how you set it up in myth), and your scan settings we would have a clearer picture and be better able to help you.

---

### Post by newlinux on 2008-09-24
I don't think this card works out of the box in Hardy. 

[http://u32.net/MythTV/WinTV-HVR-950/](http://u32.net/MythTV/WinTV-HVR-950/)

---

### Post by whitty on 2008-09-26
You're absolutely correct, it doesn't. Unfortunately, those were the very instructions I followed to set it up, and they were perfectly successful (that is, the ones here [http://u32.net/MythTV/WinTV-HVR-950/](http://u32.net/MythTV/WinTV-HVR-950/)). As for scan settings, everything. I literally set it to cable-high (as suggested by the first link on this page), then did a scan of QAM-256 until it crashed after failing to discover about 15 channels, then QAM-128, same thing, then QAM-64, which hung after about 5, then terrestrial, which also hung after about 5. I've tried spotty combinations here and there besides cable-high, but all of those failed as well. I'm incredibly frustrated that the only good experience I've had with this is using mac and elgato eyetv. I even (after much work) got mediaportal running under windows on this same computer, but there were horrific audio/video sync issues that I couldn't fix, so I turned to mythbuntu hoping it'd be easier.

Any other ideas?
Thanks, Alex

---

