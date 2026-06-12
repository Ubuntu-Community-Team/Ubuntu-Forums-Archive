---
title: "Black Screen After Disabling Onboard Video"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by em4r1z on 2008-03-22
My brand new laptop has an integrated nVidia GeForce Go 6100 video card and I am allowed to share up to 256 Mb with video within the BIOS. Well, the system information said I had 512 Mb for video (both in Ubuntu 7.10 and in WinXP SP2), thus I thought there might have been a problem with my drivers. I installed the latest but the system kept recognizing more memory for video than it actually had (it never crossed my mind that video might be using swap).

Why I had the **brilliant** idea of disabling the memory shared with video within the BIOS and now I only have a black screen. The system starts and it seems to start the OS (the access led blinks) but I can't see a thing. No error was given (and probably there wasn't.)

Any ideas of how to solve this?
My warranty covers me but I still would like to know what to do.

---

### Post by kyphi on 2008-03-22
To reactivate your graphics display you need to go into the BIOS and undo what you have done - don't forget to save your changes.

If you have RAM shared then you probably see your system RAM and the graphics chip uses as much as it needs or as much as is available.  Your graphics chip has no RAM of its own.

---

### Post by em4r1z on 2008-03-22
Thanks but I didn't express myself clear: while it may be possible to access the BIOS I wouldn't know what to do because the screen is black, just as if the LCD didn't work. I can only see a black screen right after turning on the machine, no BIOS splash, no Post screen and, obviously, no GUI for my OS. I think the OS loads correctly because the system is accessing to the disk (you can tell that by the blinking led) and because it suspends if you close the laptop and turns off if you press the Off button (I configured it this way.) The thing is that I can't see a thing!
The machine has 2 Gb of RAM, 256 Mb of which are assigned to the video card, the 'problem' is that the system said it had 512 Mb of memory for video, which couldn't be possible.

I think that if your remove the CMOS battery the BIOS resets to its default settings (which would include enabling the onboard video), but I don't want to do it because I'll lose my warranty.

---

### Post by jacob01 on 2008-03-22
check the user manual my dell has a jumper on the mobo that if you connect it to the right pins it resets the cmos but i have reset the cmos and bios by removing the battery i did this to remove a password protection. This was on a desktop, never had much experience with laptops.

---

### Post by kyphi on 2008-03-22
It is quite safe to take out your motherboard battery but remember to unplug the machine from the mains power supply first.

Those batteries last a long time but eventually have to be replaced.

This would not affect your warranty.

---

### Post by em4r1z on 2008-03-23
The machine has a warrany seal. I guess I'll just take it to the store and let them deal with this. The thing is that even if they solved this I might still have the 'original' problem: the system shows more video memory (512 Mb) than it could have (256 Mb).

Also, the LCD might be broken, I can't tell. I 'guess' it works for it worked right before I disabled the onboard video but you never know.

---

### Post by em4r1z on 2008-04-07
Well, I got my laptop back last Thursday. I had to pay $65 as the warranty didn't cover this kind of problems (or so they said.) They had to remove the BIOS and weld it back.
They also installed the latest BIOS version, where it's impossible to disable the memory assigned to video (damn, I won't be able to try that again!)

---

### Post by erginemr on 2008-04-07
Sorry for your money loss... Actually, this should be regarded as a design flaw by the laptop / BIOS developers, as it should not have been allowed for the users to disable the video memory altogether and thus render their laptop unusable, in the first place.

Anyway, I am glad that you have your desktop back...

---

