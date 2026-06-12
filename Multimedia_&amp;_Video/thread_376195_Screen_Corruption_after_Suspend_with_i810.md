---
title: "Screen Corruption after Suspend with i810"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by hey560 on 2007-03-04
I'm having a very annoying problem with the video after coming back from suspend. I have attached a picture of what happens.  The line of corruption does not go away until i reboot.

This problem occurs using Ubuntu 6.10 (gnome), feisty herd 5 with (kde).  I think it is definitely an i810 driver issue as it occurs on mutliple setups.

I have a lenovo n100 with the intel 945m graphics card.

How can I go about debugging problem? What log files can i look at? I can repeat it guaranteed if I come back from suspend. Anyone else have this problem? 

Here are some other threads with similar problems:

[http://www.ubuntuforums.org/showthread.php?t=246008](http://www.ubuntuforums.org/showthread.php?t=246008)
[http://ubuntuforums.org/showthread.php?p=2186048#post2186048](http://ubuntuforums.org/showthread.php?p=2186048#post2186048)

---

### Post by hey560 on 2007-03-04
Forgot to attach the screen shot. Here it is.

---

### Post by bloodniece on 2007-03-04
You could try disabling DPMS in xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
```
sudo nano /etc/X11/xorg.conf

```


```
Section "Monitor"
        Identifier      "Default Monitor"
       # Option          "DPMS"  #Disabled for testing. Don't change anything else.
        HorizSync       30-50   #these are my refresh rates
        VertRefresh     43-60 #these are my refresh rates
EndSection
```

All else fails.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hey560 on 2007-03-04
Disabling DPMS didn't solve the problem. Thanks for the help though.

---

### Post by fulat2k on 2007-03-06
I've got similar problem as well.  But instead of having simple lines; my entire screen goes black and whatever that's drawn on top of it doesn't get displayed properly.  Will post a screenshot of it in a while when I suspend/resume my system.  

Started happening in Edgy.  Same problem when using a fresh installation of Kubuntu Herd5

---

### Post by hey560 on 2007-03-07
i dont think thats the same bug as me fulat2k.

For everyone else, I have found a bug report filed with freedesktop.org where the i810 drivers are developed.  Here it is:

[https://bugs.freedesktop.org/show_bug.cgi?id=9381](https://bugs.freedesktop.org/show_bug.cgi?id=9381)

This is definitely the right  bug.  Now I just hope someone will fix it. If i knew how anything about X I'd try fixing it myself but alas i cannot.

---

### Post by gotcha5 on 2007-06-06
Hi, i had the same problem, My screen couldn't wake-up after suspend. The workaround is to add i8042.nomux to your bootloader's kernel parameters. In my menu.lst is like that: kernel          /vmlinuz-2.6.20-16-generic root=UUID=0ed21ce1-3de9-4a4e-afdc-25908d5bbed8 ro quiet splash i8042.nomux

For me it works!

---

