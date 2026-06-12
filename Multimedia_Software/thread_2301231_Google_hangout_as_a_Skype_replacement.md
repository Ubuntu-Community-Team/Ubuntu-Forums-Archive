---
title: "Google hangout as a Skype replacement"
date: 2015-10-31
forum: Multimedia Software
---

### Post by oygle on 2015-10-31
Have been having problems getting the microphone to work in Skype, and have seen many posts where the microphone issues is because Microsoft swapped from alsa to pulse, and they (Microsoft) currently can't fix the problem.

Therefore, am considering using Google hangouts. This wanted me to install a 64 bit .deb from

[http://www.google.com/tools/dlpage/hangout/download.html?hl=en](http://www.google.com/tools/dlpage/hangout/download.html?hl=en)

Can I add this repository to Kubuntu manually. Not sure where it is.

Hopefully there won't be any sound or video problems with Google hangouts.

---

### Post by oygle on 2015-10-31
Have followed the instructions at [http://www.ubuntuupdates.org/ppa/google_talk_plugin](http://www.ubuntuupdates.org/ppa/google_talk_plugin)  and I can see the new entry in the repository. Have done ..

```

sudo apt-get update

```

and then ..

```

$ sudo apt-get install google-talkplugin_5.41.0.0-1_amd64.deb

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-talkplugin_5.41.0.0-1_amd64.deb
E: Couldn't find any package by regex 'google-talkplugin_5.41.0.0-1_amd64.deb'

is this permissions, as the .deb is in the Downloads folder ?

Edit: yep, it was permissions. Once I moved the .deb to the correct folder and had permissions correct, it installed fine

---

### Post by papibe on 2015-10-31
Hi oygle.

The easier way is just double click the file on Nautilus (the file manager).

Alternatively,  you can install it on the command line using 'dpkg':
```
sudo dpkg -i /path/to/google-talkplugin_5.41.0.0-1_amd64.deb
```
Let us know how it goes.
Regards.

---

### Post by oygle on 2015-10-31
Thanks, I did try the double-click in Dolphin. Pressed the 'install' button but nothing happened. Anyway, was able to install it successfully using 'apt' once I moved it to /var/cache/apt/archives

Thanks for your help. Am now able to test Google hangouts. Looks like video and sound are working fine.

---

### Post by oygle on 2015-11-01
Couldn't get the microphone problems sorted out with Skype. Seems it's a common problem.

Am using Google hangout. Hasn't got all the bells and whistles of Skype, but it's simple and the sound works fine.

---

