---
title: "how to see recorded files on iphone in Ubuntu ?"
date: 2017-08-16
forum: Multimedia Software
---

### Post by shantiq on 2017-08-16
ok so i have managed to see my photos on iphone in a folder called DCIM


INSTALL:

```
 sudo apt install ideviceinstaller python-imobiledevice libimobiledevice-utils python-plist usbmuxd libimobiledevice6 libplist3 ifuse
```


and then that:
```
sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```


now i see the DCIM folder

but to my surprise when using latest Slackware 14.2  a lot more appears there i see my audio recordings too

First 2 pics on Slack

[[IMG]https://s17.postimg.org/qmk4eyaor/image.png[/IMG]]("http://postimg.org/image/qmk4eyaor/")

[[IMG]https://s17.postimg.org/nv0uocc63/image.png[/IMG]]("http://postimg.org/image/nv0uocc63/")

This pic on Ubuntu

[[IMG]https://s17.postimg.org/dwfw1v2qj/iphone_ubuntu.png[/IMG]]("http://postimg.org/image/dwfw1v2qj/")


So my question ... simply ... what do i need to do to see all of this on ubuntu  ....    am I missing software or dependencies here?

do some of you know?

---

### Post by Andreyshel on 2017-08-16
[COLOR=#111111][FONT=Ubuntu]I found [this ]("https://askubuntu.com/questions/704669/how-to-move-files-between-ubuntu-and-iphone#704677")on the internet

Now you are using gtrumb to access your iphone.
You need to use afc service instead.[/FONT][/COLOR]

---

### Post by shantiq on 2017-08-16
&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; Andrey if i have got the right idea/language :]  you put me [on the right track]("https://askubuntu.com/questions/832350/how-to-tranfer-files-between-iphone-and-ubuntu")
well explained in that page

run:

run```
 lsusb -v 2> /dev/null | grep -e "Apple Inc" -A 2
```

to find iphone UDID

```
  iManufacturer           1 Apple Inc.
  iProduct                2 iPhone
  iSerial                [COLOR=#ff8c00] 3 ca00d62380d42746b8ff8280....d1fd7b7119ca[/COLOR]


```




then open nautilus and paste in box

in my case

```
afc://ca00d62380d4274....f8280a91ed1fd7b7119ca/
```

[[IMG]https://s2.postimg.org/ku51qf08l/image.png[/IMG]]("https://postimg.org/image/ku51qf08l/")


Thanx again marked as solved!


**PS:**   recordings then need to be copied to your computer to play ...    they do not play from the folder itself

**PS2:** sometimes on new installs or in my case when I upgraded from 16:04 >> 18:04  it does not see the iphone if you unplug and replug during a session

If you are in a similar situation run:

```
 systemctl start usbmuxd
```  and enter your password; all should be good again

---

### Post by Andreyshel on 2017-08-16
> [COLOR=#000000][INDENT]**PS:** recordings then need to be copied to your computer to play ... they do not play from the folder itself[/INDENT]
[/COLOR][COLOR=#000000]

[/COLOR]
What player do you use?
Check this[ list ]("https://help.ubuntu.com/community/PortableDevices/iPhone")
Also you might need gvfs-backends installed

---

### Post by shantiq on 2017-08-16
Thanx again Andrey  I use Audacious/Xmms and when I reloaded I was able to play directly from Recordings folder

There are so many posts and articles online about Iphone and Linux and the answer is so simple ONCE YOU KNOW :]

---

### Post by #&amp;thj^% on 2018-04-03
What a great share Thanks to all.
This may even be sticky worthy! :)

---

