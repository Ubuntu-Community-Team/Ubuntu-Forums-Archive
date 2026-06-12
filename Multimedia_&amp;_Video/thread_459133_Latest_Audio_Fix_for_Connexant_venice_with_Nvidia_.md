---
title: "Latest Audio Fix for Connexant venice with Nvidia chipset(compaq v3000 and hpdv2000)"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by Poweruser20 on 2007-05-30
Hi If you own a compaq v3000 series or HPDV2000 series of laptop,After installing feisty fawn you may have noticed that the automute function when plugging the headphones does not work properly i.e the speaker is still on even though head phones are plugged in,It is required until recently to patch the alsa kernel to solve the problem,however there is a simpler way to fix the problem.

step1:ensure that you have all the build essentials installed.

step 2:download the SUSE alsa snapshot driver from 
"ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver"

*i downloaded the package 
alsa-driver-hg20070526.tar.bz2 dated 05/26/2007*

step 3:renamed it to alsa-driver.tar.bz2 for ease of installation

step 4:execute the following command from the terminal
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install

step 5:reboot the system...
sound worked well for me.Sound was clear and loud and i thank "HIazle" who reported that after reboot from windows sound worked only when ac cable was removed during reboot.i believe this is a bug and hope to find a solution for it soon.I also thank lexarrow who posted the guide eloborately for patching the alsa kernel to get automute to work .By starting from his post  i accidentally stumbled upon this solution for the sound problem.:D
I have posted this so it will be easy for users to find this.Thank you..

---

### Post by Poweruser20 on 2007-06-01
If you have upgraded to the latest kernel,the automute problem reapperas,it can be fixed by downloading and installing the latest snapshot driver 05/31/2007.from the above source.using the same procedure above.I have tested it.sound works properly without any issues with respect to automute and clarity.thank you

---

### Post by simon_ives on 2007-07-11
I downloaded the file fine but I get an error when attempting to install it.

```
./configure
```

```
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Any ideas what's going on here?

---

### Post by feiming on 2007-07-12
ok i downloaded the latest version 20070712 and ALL worked.....
when plugin earphone,it auto mute the built in speaker,mute shortcut change color,and volume shortcut also working for speaker and earphone.

haven't try the internal and external mic

---

