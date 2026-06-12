---
title: "Skype and built-in microphone low level sound"
date: 2009-11-30
forum: Multimedia Software
---

### Post by nicknefarious on 2009-11-30
I have a (see below). For three Ubuntu releases now I have had multiple problems with installing and using Skype. The last of which was a very low level of sound input even with all levels adjusted to full. I could use the sound recorder in Ubuntu to record sound no problem. The input level was good. But making a test call in Skype you could barely hear your recorded message in the replay. When I made calls no-one could hear me. I fiddled and adjusted endlessly but without success. Finally - I have just installed Skype 2.1 using these directions...

> Install Skype 2.1 beta in Ubuntu

First you need to remove the existing version of skype using the following command

    ```
sudo apt-get autoremove skype skype-common
```

Now you need to download .deb package from [[COLOR="RoyalBlue"][COLOR="Blue"]http://www.skype.com/intl/en/download/skype/linux/choose/[/COLOR][/COLOR]]("http://www.skype.com/intl/en/download/skype/linux/choose/") and install the downloaded package using the following command

    ```
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
```

For further information see this - [[COLOR="Blue"]http://www.ubuntugeek.com/howto-install-skype-2-1-beta-in-ubuntu.html[/COLOR]]("http://www.ubuntugeek.com/howto-install-skype-2-1-beta-in-ubuntu.html")

Two things to note - I am running 64-bit - so the file I downloaded and the install command I used I had to replace the "i386" with "amd64". Secondly I already had Skype 2.0 installed prior to this through the medibuntu repository.

Now everything works just fine. Internal microphone and plugged in headset. No adjustments or tweaks, nothing - It Just Works. ;)

Please note the warning that comes with the download - This is a beta. Not recommended for production systems. So it's on your head.

Hope this helps someone.

Nick

---

