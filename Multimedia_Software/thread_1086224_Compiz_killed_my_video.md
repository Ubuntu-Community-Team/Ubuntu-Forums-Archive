---
title: "Compiz killed my video"
date: 2009-03-03
forum: Multimedia Software
---

### Post by brokentroy on 2009-03-03
Hi All,

i was playing around in Compiz and when I enabled a certain feature and then my screen went crazy and i got booted out of Ubuntu.  Unfortunately, I can't remember what it was I enabled.  However, the effect it gave me is reminiscent of the when you have an old monitor on a windows box and you set the resolution too high for the monitor to handle.  With Windows, one was lucky enough to wait 15 seconds and the change would be reversed. Not so lucky with Ubuntu.  The screen when kind of black and there were a bunch of multi-colored lines through it.  

I rebooted into recovery mode and tried all of the options there and had no luck.  I also tried all of the options in the option menu at the logon screen.  nothing has worked.  any ideas what I can do?  I really don't want to have to re-install the o/s.  again!

thanks.

p/s-  I am a total newbie to this, so if you do have a solution, please be specific.  I am not familiar yet with all of the commands.  thanks.

---

### Post by brokentroy on 2009-03-03
I cannot log in at all to change anything. I booted to recovery mode and went to Root. I then ran apt-get remove compiz. I rebooted and when I logged in I now had a white screen, but got logged back out. I see my wallpaper every time I log in, but then I get either a black wierd screen or a white screen and get logged out. I will definitely get rid of the auto logon.

I ran sudo dpkg-reconfigure -phigh xserver-xorg and then I went from white screen back to black with colored lines. I reversed my progress. Is there a way to run this command and set it to low res. -plow?

---

### Post by brokentroy on 2009-03-03
Nobody has a solution to this?!  I can't use my computer.  I really don't want to have to reload the os.  I am not having any luck with dpkg-reconfigure.  Please help!

---

### Post by ender353 on 2009-03-03
Happened to me to. i had to fdisc it.
sorry dude.:(

---

### Post by ChrisMP1 on 2009-03-03
--- Never mind; I guess I didn't read your whole post ---

---

### Post by ender353 on 2009-03-03
If you have 2 hard drives you might be able to install ubuntu on the 2nd one and mount the first, then at least you might be able to get your stuff onto a flash drive or something. there might be complications with permissions though.

---

### Post by brokentroy on 2009-03-03
this is a loptop.  one hard drive.  Dell Inspiron E1705.

booted to recovery mode/root and ran lspci | grep -i vga and got this:

VGA Compatible Controller: Intel Corporation Mobile 945gm/gms, 943/940 gml Express Integrated Graphics Controller.

I'm at my wits end here.  Can't seem to find any help.  I run dpkg-reconfigure xserver-xorg from root as well and it does not give me any option to change the video driver or resolution.  only asks if I want to auto detect it.  yes or no changes nothing.  then it goes through a bunch of questions about the keyboard.

i tried booting to the logon menu and choosing options>select session>failsafe terminal  I tried editing /etc/x11/xorg.conf but when it opens it is a blank page.  i assume it's not really hitting the file.

any other suggestions. 

I was playing with graphics options in compiz.  selected something.  screen went crazy.  then got logged out.  uninstalled compiz.  no change.  tried editing xserver-xorg, no luck.  can't find anything on here or google to resolve this.

---

### Post by ChrisMP1 on 2009-03-03
Two things you can try (both in recovery mode):

1) More thorough removal of compiz
```
sudo apt-get purge compiz 'compiz-*' 'compizconfig-*'
```

2) This problem seems to be local, related to your user account only. Try this, replacing USER with a new username. It creates a new account, which you should be able to log in as.
```
sudo adduser USER
```

---

### Post by ChrisMP1 on 2009-03-03
By the way, your xorg.conf file is in /etc/X11 (with a capital X), not /etc/x11. Linux is case-sensitive; Windows is not.

---

### Post by brokentroy on 2009-03-03
thanks.  I got impatient and re-installed.  Luckily I have not made many changes to files or anything and I still have all my stuff backed up.  

That said,  should I install the Dell drivers on this laptop even though it seems to find the proper drivers already?  Is it better to let Ubuntu find what it needs or should I tell it what to use?  

thanks.

---

### Post by ChrisMP1 on 2009-03-04
Dell drivers? If you mean the ones that Dell provides with your computer, those won't work on Ubuntu. As long as it's running fine, there's no need to switch drivers.

Unfortunately, it's pretty easy to muck up X.org, and pretty hard to fix it. Any idea which Compiz setting broke your configuration?

Also, the reason 'apt-get remove compiz' didn't work is because the package 'compiz' is actually a meta-package. This means that it is an empty package, whose purpose is to pull in other packages through dependencies. That way, you can just install 'compiz', rather than the bunch of packages that make it up. Because it is really just empty, removing it doesn't do anything.

---

