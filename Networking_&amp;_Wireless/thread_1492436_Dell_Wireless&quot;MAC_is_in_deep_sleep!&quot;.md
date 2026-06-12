---
title: "Dell Wireless/&quot;MAC is in deep sleep!&quot;"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by king mint on 2010-05-24
I posted this on the Dell forum a few days ago, but there has been little response and it looks like the networking and wireless forum is a lot busier.

I am an unfortunate owner of one of the Dell XPS 1530 models that has serious wireless problems in Ubuntu. I have used every version since 8.04 and am now on 10.04, and with every version the wireless works 1 in every 4 or 5 times I turn on or restart my computer. What is so strange is that it is so erratic - mostly it doesn't work but sometimes it does.

For the first time in 10.04 there is (to my linux illiterate eye) an indication of what is going wrong: when Ubuntu starts to load an error message starts to repeat down the screen, reading:

iwl3945 0000:0b:00.0: MAC is in deep sleep!

I have seen threads about this problem for the last couple of years - any google search for Dell/Ubuntu/iwl3945/wireless or the error message shows a large number of threads indicating that many users have this problem. However I cannot find a single thread in which anyone claims to have fixed it. Please tell me that someone here has solved this problem! My Ubuntu experience has so far been miserable because of this single issue!

Many thanks,

Eric

---

### Post by ceesiebo on 2010-05-25
Hi there. I also use a Dell XPS M1530 and have the exact same problems. I installed the backport generic modules to get the latest drivers, but that only changes the errormessage (now it cannot init the EEPROM). Every versionupdate of Ubuntu just changes the errormessage or adds more deep sleep messages. I also read all the forums and bugreports, but no luck. It also does not matter which Linux-version you use (Ubuntu, Mandriva, Fedora, etc), the card just doesn't work. There is no solution (yet), only a workaround I'd rather not use and that is adding the noapic parameter in grub. I also read that an old version of Ubuntu actually works with this card (7.04 I thought), but I never tried it out. I now use a wifi-usb adapter.

What you also can try out is getting it to work via ndiswrapper. I still have to try that out.

---

