---
title: "No sound driver"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Marc Blum on 2011-05-08
I've been trying to get my HP dc5750 computer to produce sound, but so far there hasn't been any joy.:(
That is until today!:P I found out that there isn't a sound module for the card that is in the computer. I know that is no reason to be happy, but at least now I know the reason why the sound doesn't work.
My sound card is an** HBA ATI SB**.How do I go about finding a sound module[B]?
[/B]If that module can be found, how would I go about installing it?
I'm new Linux and don't know anything about programming. So would be thankful for all the help anybody can give me.

---

### Post by Buntumatic on 2011-05-08
```
sudo lspci -nn | grep -i audio
```
This will display the necessary information.

---

### Post by Marc Blum on 2011-05-08
**00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]**

This is the result of the lspci command. What's next?

---

### Post by Buntumatic on 2011-05-09
This device should work with kernel drivers since version 2.6.25.

It may require some setup, though. Here's the Gentoo discussion about it [http://forums.gentoo.org/viewtopic-t-818256-highlight-phonon.html](http://forums.gentoo.org/viewtopic-t-818256-highlight-phonon.html) , for Ubuntu this probably means you need to blacklist some other HDA modules, otherwise they will interfere.

Feel free to search Google yourself: [http://www.google.com/linux?hl=en&safe=off&q=azalia&btnG=Search](http://www.google.com/linux?hl=en&safe=off&q=azalia&btnG=Search)

---

### Post by lidex on 2011-05-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Marc Blum on 2011-05-14
Buntumatic thank you for your help. Now where do I find the "drivers" page, directory or what ever it is that is mentioned in that Gentoo article?

---

