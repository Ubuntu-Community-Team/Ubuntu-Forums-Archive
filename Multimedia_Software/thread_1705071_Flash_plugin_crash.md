---
title: "Flash plugin crash"
date: 2011-03-11
forum: Multimedia Software
---

### Post by Ajay Ramaseshan on 2011-03-11
Hello,

I have Ubuntu 10.10 32 bit. and am facing this problem . I cant play any Youtube video on any browser, Fireox, Google Chrome or Opera. It shows a grey screen where the video is supposed to play. Reloading the page again and again does not change the situation.

On some other websites ( like bbc.com) , the video plays, but upon Fullscreening , the plugin crashes. 

I have tried reinstalling the plugin many times but to no affect, Also tried Flash-Aid Addon for Mozilla Firefox but even that does not work.

Can anyone help me out?

Ajay

---

### Post by sammiev on 2011-03-11
If you are using No Script with FireFox, then select options and give permission. GL :)

---

### Post by Orographic on 2011-03-11
Have a look through the topics here, you will find that its a problem with the latest Flash update, or at least that is the most likely issue. The problem is somewhat different in each case.

You can downgrade to the previous version of Flash and then lock that version. For me, it only crashes in YouTube in Firefox and a reload fixes it. No problems in other browsers.

---

### Post by Ajay Ramaseshan on 2011-03-23
> **Orographic said:**
> Have a look through the topics here, you will find that its a problem with the latest Flash update, or at least that is the most likely issue. The problem is somewhat different in each case.

You can downgrade to the previous version of Flash and then lock that version. For me, it only crashes in YouTube in Firefox and a reload fixes it. No problems in other browsers.

Other flash contents sites ( like bbc,com etc ) crash on full screening. SO I forcibly deleted the plugin files and downgraded to 10.1 r999.

Now Youtube videos work only in Firefox there also it gets stuck for a few seconds when I switch from Full Screen mode to Normal mode. And other flash content like ( bbc, etc) refuses to play saying that I have a lower version of Flash. On other browsers like chrome and Opera. it just displays a message where the video should be playing "An error occurred please try again later"..!!!

Getting really irritating but thankfully managed to make it work in Firefox atleast.

---

### Post by Ajay Ramaseshan on 2011-05-02
I have installed the latest version of the Flash plugin .. 10.3.181.5. Only when I disable hardware acceleration in the Flash player settings, fullscreening works sometimes. But many times on fullscreening the video hangs and system stops responding..I am forced to press the power button to shutdown the system .!

Could anyone please help me out??

---

### Post by TenPlus1 on 2011-05-02
A friend had the same problem which was onyl fixed by downgrading to flash player 10.1...  It seems to be a bug in the flash plugin on certain gfx cards with hardware acceleration and vdpau support...  My old nvidia 6600 seems to work fine though...

---

### Post by no2498 on 2011-05-02
try installing grease monkey for fire fox plugin

---

### Post by Ajay Ramaseshan on 2011-05-02
> **no2498 said:**
> try installing grease monkey for fire fox plugin

Can you please tell what this Greasemonkey add on do ??

---

### Post by Ajay Ramaseshan on 2011-05-03
Hello

The culprit of this full screen crash was the Proprietary FGLRX Driver I had installed from Ubuntu 's 'Additional Drivers" section for my ATI Graphics Card 5000 Radeon. When I uninstalled this driver and used only the Intel Chipset Driver, it works properly even with 3d acceeleation enabled. Looks like there is a bug in the FGLRX Driver

This time "Additional Drivers" feature whch was introduced in Ubuntu 10.10 only I think, has brought "Additional Problems"!!

---

### Post by garvinrick4 on 2011-05-03
If you get in a bind just remove all the flash by products that wind up all over the
place by trying to install 3 different ways and then install, keep it simple.
First line just stops all firefoxs that could be running rest removes junk and then
install from Ubuntu software center.

sudo killall -9 firefox
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
NOW INSTALL FROM REPOSITORY:
#If you want to download a tarball from Adobe extract and run just these two lines;
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

*Sometimes you just got to clean it all up and put a new package in. Works.

---

