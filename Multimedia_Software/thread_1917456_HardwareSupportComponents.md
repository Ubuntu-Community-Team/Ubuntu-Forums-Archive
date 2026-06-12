---
title: "HardwareSupportComponents"
date: 2012-01-30
forum: Multimedia Software
---

### Post by dimas869 on 2012-01-30
my graphic card was working fine but i thought i could have better performance by installing a graphic media acelarator so i did install EMGD 1.8 doing this:
sudo add-apt-repository ppa:gma500/emgd-1.8
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf

when i reboot no graphic display no more so i did removed the installation running ubuntu in recovery mod by typing:

sudo apt-get remove xorg-emgd emgd-dkms

but still didnt work so i guess something still installed that cause the problem and is extrange because when i run ubuntu i see the purple screen but no the letter that indicate is loading and after the screen goes to sleeping mod and then when i press Ctrl+Alt-Del i see the letters and reboot

anyway...

i also try

sudo dpkg-reconfigure xserver-xorg

but nothing

i would really appretiate if someone walk me throuw to get it back the way it was before i did the EMGD 1.8 installation

i am using ubuntu 11.10

thanks in advance

---

### Post by dimas869 on 2012-01-30
i did a lspci -v and i get the my video card is a ATI Technologies Inc RC410 
Radeon Xpress 200

and in save mod throw me a message saying "unable to enumerate USB device on port 8
so i guess i did not suppose to use that driver.

could someone help me get it back to work?

---

### Post by dimas869 on 2012-02-02
never mind i did re-installed the whole system

---

