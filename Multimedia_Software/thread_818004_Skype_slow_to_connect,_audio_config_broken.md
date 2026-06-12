---
title: "Skype slow to connect, audio config broken"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Thirsty Ferret on 2008-06-04
Hello everyone =)

I have had no problem with Skype in the past, since Hardy it installed first time and has worked since. Last week I got a new bluetooth adapter and was working trying to get my Sony bluetooth headphones to act as a Skype headset...

Anyway, the other day when I started Skype again it took what seemed like forever (probably 3 - 4 minutes) from the sign-in page disappearing to my contacts loading and it starting. I then sent some messages, and they didnt send for over 2 minutes, and replies were equally slow. Obviously this isnt a good situation to be in for instant messaging!

So, I tried uninstalling with "sudo apt-get remove skype" and then reinstalled from the Deb on the Skype website. This did the same thing, so I removed again, added the Medibuntu repos and installed from there - still no luck. Then I tried purging it, then purging and deleting the .Skype directory in the home folder, but still no luck, it takes ages now!

Is there anything I can do to wipe the audio settings for it (which I think may have broken it) or is there another problem here?

Additionally, whenever I went in to Skype Options, all of the sections worked other than audio config which caused a crash.

Thanks for your help :)

Chris

---

### Post by aum11 on 2008-06-04
Hi Chris,

I have exactly the same problem and have so far been unsuccessful in trying to gat a fresh install happening.  Will continue to try and will let You know if I have any success.

---

### Post by Thirsty Ferret on 2008-06-04
Ok thanks very much :) I would very much like to sort this as my phone bill is taking a real hammering!

I will continue to try too, and post here if I have any luck.

---

### Post by FromWithin on 2008-08-11
Did anyone manage to get to the bottom of this problem? I've had the same thing since Skype 2.0.0.72.

Edit: I reinstalled (from medibuntu) and everything seems okay now.

Edit2: I spoke to soon there. It went slow again. I started it from the command line and was getting audio errors regarding a bluetooth device. Going into Skype options and trying to bring up the Sound Devices page made Skype hang. So I went to the Bluetooth Manager and disabled the Audio service and everything is fine now.

---

### Post by _Kesler_ on 2008-08-20
instead of using the repo why not try the latest skype version.

download skype from [http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/)

for 32bit install from xterm:
sudo dpkg -i /skype-debian_2.0.0.72-1_i386.deb

for 64 bit install from xterm:
sudo dpkg -i --force-architecture /skype-debian_2.0.0.72-1_i386.deb

Download getlibs from [http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb)
Double click downloaded file to install it.

run "getlibs /usr/bin/skype" from terminal

for both 32bit and x64 (1 and/or 2 may not be necessary)
1) open volume control and click file/change -- choose device/opt 1 (edit/preferences -- check all)

2)from xterm type alsamixer change Digital to "Digital" (where it currently says Analog above Digital)

good luck!

---

