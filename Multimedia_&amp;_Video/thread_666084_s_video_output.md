---
title: "s video output??"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by broekskw on 2008-01-13
hi all running ubuntu 7.10 with a ati 9200 with s-video output,watching a movie on my pc screen hooked up the s-video cable from card to tv but no picture, selected correct input on tv but still no luck, is there a setting in ubuntu that i need to set?

thanks

---

### Post by randcoop on 2008-01-13
Svideo out in Ubuntu with ATI is very difficult.  I don't think you'll find a way to just click a setting and then use your TV.

I use two different xorg.conf scripts to make my svideo work with ATI.  When I want to use the TV, I copy the TV on file (xorg.conf.tvon) to xorg.conf and then restart X (CTRL-AlT-BACKSPACE).  However, using my files, you don't get dual screens; the TV goes on and the LCD goes off.  Then, when I want to switch back, I copy the xorg.conf.tvoff file to xorg.conf and restart X.  

This works perfectly (except for the shortcomings of having to restart X and not having dual screens).  Here's the relevant sections of TVoff and TVon:

TV On:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tv"
	Option	    "TVStandard" "VIDEO"
	Option	    "ForceMonitors" "crtl,tv"
EndSection

TV Off:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tv"
	Option	    "TVStandard" "VIDEO"
	Option	    "ForceMonitors" "crtl,notv"
EndSection

So it's literally just the ForceMonitors option that changes.

The xorg.conf file is in /etc/X11/.  

CAUTION CAUTION CAUTION:

I do not promise this will work for you.  Changing xorg.conf can make your X display unviewable.  PLEASE PLEASE PLEASE make a backup of the working xorg.conf before trying any of this.  Then, if something goes wrong, you can restore it from the command line.

---

### Post by broekskw on 2008-01-13
thanks for your reply randcoop. did go into display setting and selected second display but had no luck until i rebooted this morning, know all i get after the ubuntu splash screen is a black screen, the login screen will not come on, i think it,s trying to use the second display to fire up but also this screen is black, so tried to restart in recovery mode and everything looks like it loaded up fine but just at the end i have a command window left, i think i need to type in a command line to get back to my default screen display,

what if any is the command to do this , reset back to default display:confused:

do not want to reinstall ubuntu from live cd please help someone:popcorn:

---

### Post by broekskw on 2008-01-13
boy you got to love this site:popcorn::)

did a search and found what i needed to input on the command line,up and running again

again great site and thanks to all who contribute here:popcorn:
10 out of 10

---

