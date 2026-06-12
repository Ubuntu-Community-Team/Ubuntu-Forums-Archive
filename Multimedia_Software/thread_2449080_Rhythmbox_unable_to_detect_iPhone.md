---
title: "Rhythmbox unable to detect iPhone"
date: 2020-08-19
forum: Multimedia Software
---

### Post by xmodx2 on 2020-08-19
Hello, 
   
  i need help, Rhythmbox is unable to detect iPhone music files,

Steps checked
1. iPhone charging
2. iPhone Trusted

OS: Ubuntu 20.04.1

Screenshot of Rhythmbox
[https://snipboard.io/tKm5Fi.jpg](https://snipboard.io/tKm5Fi.jpg)

---

### Post by shantiq on 2020-08-21
ok xmod personally got not much love/time for or knowledge of Rhythmbox so no pointers from me on this one 
but here is what i do for music on iPhone currently SE:

I use VLC mobile which allows you to play movies too and all lossy/lossless formats

This is a howto i knocked up [a while back]("https://ubuntuforums.org/showthread.php?t=2392292&p=13768299#post13768299")

Also explained maybe more clearly [here]("https://askubuntu.com/questions/812006/how-can-i-mount-my-iphone-6s-on-ubuntu-16-04/1057237#1057237")

These are shots of how it all looks [this is on LXDE will look tad different on other DEs]:

[[IMG]https://i.postimg.cc/YGvpNxvQ/1.png[/IMG]]("https://postimg.cc/YGvpNxvQ")[[IMG]https://i.postimg.cc/LYGmxZPw/2.png[/IMG]]("https://postimg.cc/LYGmxZPw")


[[IMG]https://i.postimg.cc/ts9pvb1q/IMG-2264.png[/IMG]]("https://postimg.cc/ts9pvb1q")[[IMG]https://i.postimg.cc/w786JLgs/IMG-2265.png[/IMG]]("https://postimg.cc/w786JLgs")[[IMG]https://i.postimg.cc/tnPpwCtT/IMG-2266.png[/IMG]]("https://postimg.cc/tnPpwCtT")[[IMG]https://i.postimg.cc/ykm7Tx8p/IMG-2267.png[/IMG]]("https://postimg.cc/ykm7Tx8p")[[IMG]https://i.postimg.cc/MvF5DCWn/IMG-2268.png[/IMG]]("https://postimg.cc/MvF5DCWn")


Sincerely hope it helps:   VLC is way more elegant on iPhone than other software but this is a personal view

---

### Post by xmodx2 on 2020-08-21
Thanks so much shantiq, using VLC as alternative im cool with the idea :) 

i did try to run ```
sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils python-plist:i386 usbmuxd libimobiledevice6 libplist3 ifuse
```

but i got this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-plist is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python3-plist:i386 python3-plist

E: Unable to locate package python-imobiledevice
E: Package 'python-plist' has no installation candidate

```

im using 
```
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    foca
```

---

### Post by shantiq on 2020-08-21
simple fix look what it sez in the message [20.04 uses python3 not python my howto was from 2 years ago :]

[I][B]to replace
[/B][/I]

so run:

```
sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils  usbmuxd libimobiledevice6 libplist3 ifuse python3-plist:i386
```   if you are on a 32-bit install

OR

```
sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils  usbmuxd libimobiledevice6 libplist3 ifuse python3-plist
```   if you are on a 64-bit install


and then carry on with howto :KS here below copied out in full and updated
Best of luck you should be fine now ...


[B]================
================
================


[/B]Tested on iPhone 4S on 16.04 and now SE on 18.04; no reason to believe it will be different on 6 or later versions ... asking others it works all the way to iPhone 7 and probably up to latest  


Fairly simple route:


&#10122; INSTALL:


    ```
sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils  usbmuxd libimobiledevice6 libplist3 ifuse python3-plist

```

if on a 64-bit install.


    ```
sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils  usbmuxd libimobiledevice6 libplist3 ifuse python3-plist:i386

```

if on a 32-bit install.

===

&#10123; you may need to do this too [one line at a time]:
    ```

sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown

```


&#10124; in Terminal to see your iphone address:

```
lsusb -v 2> /dev/null | grep -e "Apple Inc" -A 2

```

You will see something thus:

```

iManufacturer           1 Apple Inc.  
iProduct                2 iPhone  
iSerial                 3 ca00d62380d42746b8ff8280....d1fd7b7119ca 
``` 


&#10125; Open Nautilus

enter the iSerial from above:

add: afc://


    ```
***afc://***ca00d62380d4274....f8280a91ed1fd7b7119ca/

```

NOW you see your files. **[SIZE=1]*Photos are in DCIM folder*[/SIZE]**


&#10126; As an embellishment you could install VLC Mobile
from App Store FREE of course which will let you play formats itunes cannot handle Flac Wavpack etc


you will see/place the music files in *Documents on iPhone* next to *iPhone* on left of page [This is on LXDE; must look similar in other Desktop Environments]


=== TIP ===


If iphone VLC files at any point are not visible on your PC; I found this brings them   back:unplug phone run command below then replug  


    ```
sudo usbmuxd --verbose -f
```

---

### Post by xmodx2 on 2020-08-24
thank you i was able to install this, and i need further help on the later step

&#10125; Open Nautilus

enter the iSerial from above:

add: afc://

it seems im abit lost looking for nautilus and where could i add this afc://

PS: system detected my phone and showing serial on command lsusb -v 2> /dev/null | grep -e "Apple Inc" -A 2

---

### Post by xmodx2 on 2020-08-24
thanks shantiq this is all sorted out. this alternative works for me, im going to use VLC for now :)

Question:  
1. if i am to mass delete those music already on my phone to save space  how? as i cant see them on VLC browser only on iphone music app
2. do i have to manually add those music or manage playlist on phone? is there a way to do it on computer? and sync the settings just like on iTunes?

---

### Post by shantiq on 2020-08-25
hi there xmodx2 

I do not have iTunes anywhere so not much I know about this but if you look in original folder and check the iTunes folder your regular music files might be there then you can cut them out and put them in the VLC folder. Have a go and please tell us if it works. Thanx



from &#10122;  [[IMG]https://i.postimg.cc/DWShpr0q/1.png[/IMG]]("https://postimg.cc/DWShpr0q")              to     &#10123;  [[IMG]https://i.postimg.cc/LYGmxZPw/2.png[/IMG]]("https://postimg.cc/LYGmxZPw")

---

### Post by xmodx2 on 2020-08-25
i could see Music added on VLC but i could not see music added on iTunes

[ATTACH=CONFIG]286798[/ATTACH]

---

### Post by shantiq on 2020-08-25
I meant go into the folders as shown in previous post and see if you can shift the Music files from iTunes if they are visible and place them in your VLC files

---

### Post by xmodx2 on 2020-08-25
thanks for the patience on helping me on this,

here only picture files are visible on DCIM folder 
[ATTACH=CONFIG]286799[/ATTACH]

---

### Post by shantiq on 2020-08-25
not DCIM   when you look in your ***afc://***[COLOR=#000000][FONT=&amp]ca00d62380d4274....f8280a91ed1fd7b7119ca/   you can see this and there is a iTunes folder there see. Look inside the subfolders and see if your iTunes music is there. If it is cut them out of there and put them in your VLC folder

[/FONT][/COLOR][COLOR=#000000]I hope this is understandable
[/COLOR]

[[IMG]https://i.postimg.cc/DWShpr0q/1.png[/IMG]]("https://postimg.cc/DWShpr0q")

EDIT:   ha   i went into the default Desktop Environment and I see all the options there are VLC or DCIM    none of the other options i was talking about. No wonder you cannot see them ...

Not sure what to suggest now :D  

[[IMG]https://i.postimg.cc/fkf87W1j/Screenshot-from-2020-08-25-14-10-16.png[/IMG]]("https://postimg.cc/fkf87W1j")


[[IMG]https://i.postimg.cc/7bkBTJtZ/Screenshot-from-2020-08-25-14-10-55.png[/IMG]]("https://postimg.cc/7bkBTJtZ")

---

