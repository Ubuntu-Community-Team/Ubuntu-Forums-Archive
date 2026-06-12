---
title: "Guitar pro 6 not working in Ubuntu 13.04 (or Ubuntu 12.10 / 12.04)"
date: 2013-04-12
forum: Multimedia Software
---

### Post by Finn bjerke on 2013-04-12
Install is ok, but the programme does not start. I had the same problem on Ubuntu 12.04 and 12.10, so here is the fix:

    Rename or delete ./opt/guitarpro6/libz.so.1 and replace it with a  softlink to ./lib/i386-linux-gnu/libz.so.1 that way you will not screw  up dependencies in the Ubuntu 13.04 system. 

Installl Gnomecommandor start is as "root"  
navigate to  ./opt/guitar pro/libz.so.1   
delete libz.so.1 
Start Terminal and make a soft link to ./lib/i386-linux-gnu/libz.so.1 like this copy this:

```
sudo ln -s /lib/i386-linux-gnu/libz.so.1 /opt/GuitarPro6/  
```

-----------------------------------------------------------------------------

alternatively you can do the same thing this way:
Press windows button and write gksudo nautilus 
enter your codeword for Ubuntu 
now you can navigate using nautilus and change things you are now root administrator (close to god if you like) 
go to ./lib/i386-linux-gnu (this is a folder) using nautilus find the file named libz.so.1 rightclick on it. 
Make a shortcut or what ever its called in your language. 
Cut the shortcut out and insert it in the guitar pro folder thus: 
click on libz.so.1 then press ctrl+x 
go to ./opt/guitar pro using nautilus 
delete the local libz.so.1 or rename it libz.so.1(bis) 
Then pres ctrl+v (inserting the shortcut file from the previous position ./lib/) 

 

The Guitar pro supporter team dont care about Ubuntu they seem lazy or arrogant or both. If thangs go wrong its your problem not mine, however I hope it helps go  play guitar now and have fun.

---

### Post by kai-lessmann on 2013-08-05
Hey Finn, 

thanks for the fix, it worked for me. **But!** I reallyreally need to caution against using a soft link: I did use a soft link, and ran the Guitar Pro Updater afterwards. After that, my ubuntu system was broken!

Apparently the Guitar Pro Updater (which needs root privileges to run) had pulled a "new" libz and -- because of the link -- replaced the ubuntu system libz. (BTW, to fix this, I downloaded the corresponding package, called libz1g I believe, on a different machine, extracted libz.so.1.2.27 and copied it, using an USB stick, to the corrupt system.)

I have now copied (not linked) libz.so.1 to the Guitar Pro directory. 

But thanks again for your post! Guitar Pro works nicely now. 
cheers!  kai

---

### Post by donnie.rose.dr on 2013-11-07
Thanks for the post.  Copying the libz.so.1 into the [COLOR=#000000][FONT=Ubuntu Mono]/opt/GuitarPro6/ worked fine[/FONT][/COLOR]

---

### Post by swampy1979 on 2013-11-12
Hi, I have had loads of problems with this especially on 64bit versions.

So I have written a guide, (my first one so go easy if I messed something up!) as this software is excellent but Arobas are crap at doing packages for linux or just can't really be bothered, maybe they only sell a tiny amount, still credit where credit is due, at least they do a linux version so Arobas I forgive you, and your software is great, well when you finally get it to work anyway.

Well here goes.

I am running ubuntu 13.10 saucy salamander 64 bit, with al the extra repos enabled in synaptic, I have synaptic installed obviously? sorry!

Anyways I have installed this software on a fresh install purely as I was worried about all the libraries that will be shuffled around and changed through dependencies as it requires a lot of 32bit packages, so I can guarantree it works on the above if you follow along exactly.

I cannot guarantee the same on a non-new install so do so at your own risk!

Firstly I installed synaptic! as I always do, don't really need it but do as I did and it will work! It makes searching i386 packages a breeze, plus I really don't like software center, it should be in Windows or Mac 
THIS IS HOWEVER MY OPINION ONLY I DO NOT ASK YOU TO AGREE OR CARE! NOR DO I CLAIM I AM RIGHT EITHER.

root prompt throughout unless stated otherwise
# apt-get install synaptic -y

Open synaptic, goto settings, repositories and tick everything on Ubuntu Software tab, and same again on Other Software tab then click reload.

Now close synaptic.

# apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0

# apt-get install libc6 libstdc++6 libasound2 libxml2 libxslt1.1 libportaudio0 libportaudio2 libglu1-mesa gksu libssl0.9.8

# apt-get install libc6:i386 libstdc++6:i386 libasound2:i386 libxml2:i386 libxslt1.1:i386 libportaudio0:i386 libportaudio2:i386 libglu1-mesa:i386 libssl0.9.8:i386 -y

# apt-get install libpulse-dev:i386 libxrender-dev:i386 libfreetype6-dev:i386 libSM-dev:i386 libfontconfig1-dev:i386 libasound2-dev:i386 libasound2-plugin-equal:i386 libasound2-plugins-extra:i386 -y libasound2-plugins:i386

download guitar pro 6 from some source, the version I installed is gp6-full-linux-r11201.deb, however to gety it to work you have to remove a dependency as there is no working gksu:i386 or if there is it evades me!

Open the deb package with archive manager and extract the contents, then you need to:
# chown -R root:root gp6* directory you just extracted

Open the DEBIAN/control file with gedit as root

# gedit DEBIAN/control

Under dependencies delete reference to gksu and save the file to the extracted directory overwriting the original file.

Now you need to rebuild the deb file for installation, from the directory above the extracted files in a terminal run:

# dpkg-deb -b . ../guitrarpro6-version-number.deb

Use correct file names obviously, if it does not work you are in the wrong directory or are using the wrong file name.

Now lets install the lettle bugger!

In the same directory as your new gp6*.deb file run from a terminal:

# dpkg -i gp6-full-linux-r11201.deb

Again use apropriate file name.

Once it is installed there are more tweaks to get it working.

goto /opt/GuitarPro6 in a terminal as root and run:

# mv libz.so.1 libz.so.1.BAK

As ironically the one provided with GP6 does NOT work, you could just delete it too if you cannot stand the chaff.

Now for the soundbanks!

copy your soundbanks to /opt/GuitarPro6/

Then again from a terminal run using apropriate file name, I had 2 soundbanks so I ran both:
/opt/GuitarPro6/GPBankInstaller /opt/GuitarPro6/Soundbanks.gpbank /opt/GuitarPro6/Data/Soundbanks/
/opt/GuitarPro6/GPBankInstaller /opt/GuitarPro6/Banks-r370.gpbank /opt/GuitarPro6/Data/Soundbanks/

it took quite a while to complete, bot once its done you are also done! welldone you have a working copy of GP6 with soundbanks installed.

Oh actually there is one caveat, which I will leave to someone else to figure out if I may, you have to run it as sudo or root, otherwise it bombs out after the jingle and a momentary white box.

But other from that slight niggle, at least I can finally write off the need for windows, or wine for gp6 yipee!!!!

---

