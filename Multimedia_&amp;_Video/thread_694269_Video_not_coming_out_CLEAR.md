---
title: "Video not coming out CLEAR"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by sujahat on 2008-02-11
Okay, I have been using Ubuntu for a while now, got Compiz and everything installed and working... life is good.. however..  just have a small question... I have my ATI drivers installed.. screen is at 1650 x 1050 resolution.. no matter which player I use Xina, Mplayer or my fav VLC,.. the video is good.. just not CLEAR..


I am attaching a screen shot I took of the Video, both on VLC, one is in Windows and the other with the PAUSE sign is Ubuntu...
FYI:Screen shot taken after runing the Metacity --replace command from ALT+F2, which turn's off Compiz..

I googled it.. did a search in this Forums, still cant find the right answer..

and my " sudo lshw -C video " is


sujahat@sujahat-desktop:~$ sudo lshw -C video
[sudo] password for sujahat:
  *-display
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

and my " lspci | grep VGA " is
sujahat@sujahat-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c1


I have a ATI Radeon HD2400 XT Video card, I did install ATI Catalyst Control Center, it see's all the drives.. and I'm assuming its working fine... on the other side in System >  Administrator > Screen and Graphics in the Graphics tab is showing that my driver is fglrx .. any idea..... and when I push the TEST button the screen goes all black and white grains... and I cant see a thing..

so this got me thinking that I have a 256MB ATI Radeon HD2400 XT Video card.. and I cant see a clear VIdeo.. so there is some thing wrong.. and beside's that when I use gtk-recordMyDesktop i cant move the cube and there is a bit of a lag and its slow... so any idea what could be wrong..

your help is appreciated.

Good day.

---

### Post by sujahat on 2008-02-12
any one?

---

### Post by xzero1 on 2008-02-13
It seems to me the windows video is filtered more. When running windows, the driver may take advantage of hardware on your video card for this. Vlc has some video filtering or post processing options you might try.

---

### Post by SunnyRabbiera on 2008-02-13
the main culprit is most likely the ATI card...

---

### Post by sujahat on 2008-02-14
thanks for the reply....
I do feel that there is some thing wrong with the ATI card.. cant seem to get what it could be... any idea which filter's i could try in VLC?

---

### Post by xzero1 on 2008-02-14
Both vlc and mplayer have video post-processing options that might be useful. Look under the video tab in vlc or the misc tab in mplayer.

---

