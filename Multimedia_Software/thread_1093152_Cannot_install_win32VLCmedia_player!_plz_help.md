---
title: "Cannot install win32/VLC/media player! plz help"
date: 2009-03-11
forum: Multimedia Software
---

### Post by kunaly2k on 2009-03-11
Friends i am a newbie to linux and downloaded Xubuntu intrepid ibex but was frustrated to extent when i came to know that i cannot play mp3's and videos! After some research i downloaded the win32 and some lib codecs and vlc player & media player in .deb format but whenever i try to install any of them it shows a message "Dependency not satisfied" :-( plz friends help me out with this thing by any helpful links or softwares! PLZ!
P.S. My pc is not connected to net so please guide me through the offline method of installation. Thanks

---

### Post by Reeman on 2009-03-11
> **kunaly2k said:**
> Friends i am a newbie to linux and downloaded Xubuntu intrepid ibex but was frustrated to extent when i came to know that i cannot play mp3's and videos! After some research i downloaded the win32 and some lib codecs and vlc player & media player in .deb format but whenever i try to install any of them it shows a message "Dependency not satisfied" :-( plz friends help me out with this thing by any helpful links or softwares! PLZ!
P.S. My pc is not connected to net so please guide me through the offline method of installation. Thanks
  
As far as VLC goes it requires quite a few media libraries that are not installed by default with Ubuntu. I would suggest trying another distro that installs the "proprietary codecs" and player by default. [Mint]("http://www.linuxmint.com/") Linux is one that comes to mind. It is an Ubuntu varient so is very user freindly. It is also available in 86_64 if that is what you need. It also runs as a live CD so you can check it out without installing it first. 

If you really are a sucker for punishment get the ubuntu debian build essential packages then try compiling VLC from source. The VLC source is old school and just requires that you do a  "$./configure", "$make" and a "$sudo make install" no scons or other special build requirements other that all the development libraries that are not install by default with the Ubuntu build-essential.  This way you will see that it requires about 10 development libraries and special libs that are not there by default. I have already done this as the VLC package in the Debian repositories is dated. The newer VLC is much closer to a 1.0 release and runs much better than the debian package ...which I ditched!

---

### Post by kunaly2k on 2009-03-12
thanks but i am just a newbie to linux so downloaded source files from vlc website but dont know how to make it a deb package! I checked out mint linux and liked it also, does it comes with divx & xvid codecs in XFCE version also? Thanks for your help! Good day

---

### Post by AXeS on 2009-03-13
hey kunaly2k,i got ubuntu ibex which is,if im not mistaken,pretty similar to Xbuntu right.

ok i dont have a connection either but installed vlc manually last night by downloading the files one at a time -took me a while but i got it working-
.At least it plays what i need it to,avi wmv,mp3...etc basically 4 entertainment.

So what i did was download fr0m site 'packages.ubuntu.org',i think,the program and the missing dependencies. how i did that was,lets say i search under intrepids .deb files.i looked for 'vlc',it got a couple of hits but im looking for the graphic version.
went there and saw what the dependencies were.(here is the long part)
wrote it all down for each and every package,checked the dependencies.

needless to say it took me some patience and a couple of pages. 

booted ubuntu,started terminal and used 'aptitude'.
the 'L' key is for search... and checked all i wrote down.

downloaded what i didnt have and voila 9months later someone was pregnant -just kidding- 

please note: there might be a better way i dont know about,because im still n0obish.
i downloaded all the files using my cellphone...and right now replying using my cellphone browser.

go0dluck and h0pe this helps.

---

### Post by AXeS on 2009-03-13
now i feel kinda dumb taking all that time, here is a way to generate what you need to install : [http://ubuntuforums.org/showthread.php?t=1078542&highlight=offline+installs](http://ubuntuforums.org/showthread.php?t=1078542&highlight=offline+installs)

---

### Post by kunaly2k on 2009-03-13
thanks bro very much! but i didnt got the part the you wrote all the packages! i too downloaded vlc source files but dont know how to compile into a package, i am also downloading various dependencies and files for vlc and codecs lets see what happens! Thanks

---

