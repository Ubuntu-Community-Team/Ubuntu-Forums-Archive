---
title: "what does &quot;out of range&quot; message mean exactly &amp; how to eliminate it ?"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2007-12-04
I am trying to get **Gutsy** installed on a machine that is using an ATI Radeon 9200 video card and a Viewsonic model 702b LCD monitor.  

I have tried both the DESKTOP/live install and also the ALTERNATE install version and I can not seem to get rid of this "out of range" message that appears on the monitor after the GRUB messaging is display and before the machine gets to the login prompt and it is also displayed shortly after I do a restart or shutdown command.  Please note that I do not have this problem with earlier versions of Ubuntu on this same hardware.

If I install from the ALTERNATE version, the video seems to work perfectly once I get to the Ubuntu desktop.  The glxgears command shows that I am getting good speed (for this card) and the glxinfo command shows that direct rendering is enabled.

Does this displaying of this "out of range" message simply means that the video resolution, etc. is not proper STRICTLY/ONLY for the bootup process of Ubuntu and that once the machine actually gets the O/S (Ubuntu) loaded there is nothing to be concerned about the functioning of the video ?  But even if the aforementioned is true, is there some simple way (with out having to reinvent the wheel) to get rid of this "out of range" message during the boot process ?

Thanks.

---

### Post by NT4usB on 2007-12-04
It has to do with the resolution of the graphic (trying to be) displayed during the boot process being out of range.
There are fixes posted somewhere...
For fun, hit Esc when grub comes up. Edit the kernel line and remove the stuff at the end... quiet and splash or something. (it all comes back next time you boot)
You'll see all the booting going on and no out of range error.
I've never bothered to fix it. Just ignore it until x sorts itself out and boots.

---

### Post by atlfalcons866 on 2007-12-04
out of range means the monitor dosent support the resolution the computer want to display. It does this to protect the monitor from damage.

---

### Post by wpshooter on 2007-12-05
> **NT4usB said:**
> It has to do with the resolution of the graphic (trying to be) displayed during the boot process being out of range.
There are fixes posted somewhere...
For fun, hit Esc when grub comes up. Edit the kernel line and remove the stuff at the end... quiet and splash or something. (it all comes back next time you boot)
You'll see all the booting going on and no out of range error.
I've never bothered to fix it. Just ignore it until x sorts itself out and boots.

I took the "quiet" out of the file but I STILL see "out of range" !!!

---

### Post by NT4usB on 2007-12-05
First, lets make sure I understand you original post...
You are getting the out of range error _only while it's booting_ but it eventually boots to a working xscreen and the video is ok after that?

If so, removing the _quiet_ and _splash_ should stop the bootimage from loading when it boots. Then you get to watch all the booting up processes scroll down the screen.

Look for posts on bootsplash to fix it permanently.

Are you using a KVM?

If the xserver never loads, try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from a terminal.
Ctrl+Alt+F1 and login to term.

---

### Post by wpshooter on 2007-12-05
> **NT4usB said:**
> First, lets make sure I understand you original post...
You are getting the out of range error _only while it's booting_ but it eventually boots to a working xscreen and the video is ok after that?

If so, removing the _quiet_ and _splash_ should stop the bootimage from loading when it boots. Then you get to watch all the booting up processes scroll down the screen.

Look for posts on bootsplash to fix it permanently.

Are you using a KVM?

If the xserver never loads, try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from a terminal.
Ctrl+Alt+F1 and login to term.

Yes your understanding is right on the money, except that after I sudo gedit /boot/grub/menu.lst and remove both quiet and splash one at a time and rebooted after each remove, I still saw exactly the same thing that I had before, i.e. "out of range", did not see any booting scripts like we used to see on the older versions of Ubuntu.  Am I removing these command from the correct place.  It sort of looks like to me that they are commented out in the file to begin with, in that, the line has a # in front of it.  As I remember it was # foblition=quiet,splash

No, no KVM.  Just one analog LCD monitor hooked to one internal ATI Radeon 9200 video card.  This a not really an older monitor at all, and according to what I see on the specs on it, it should be able to handle just about any freqency range that Ubuntu might possibly be trying to use.

Should I still try that dpkg command.  I never really know how the questions that are posed by that command are supposed to be answered.  It asks a lot of stuff that I don't even know what it is talking about !!!   They really need to come up with a better solution to these kind of problems than this.

Thanks.

---

### Post by NT4usB on 2007-12-05
So, all were dealing with is the annoying out of range error during boot. I just ignore it. 
There's tons of discussions and fixes posted if you want to mess with it. [posts]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+gutsy+usplash+%22out+of+range%22&btnG=Search")
Don't run dpkg-reconfigure, that's only for when your xserver won't start at all...
I've only used it once since I do all my x fixing by editing xorg.conf direct. The -phigh makes dpkg skip most of the questions, iirc.

If you Ctrl+Alt+F1 while you're seeing the out of range error, you'll see in the terminal the display resolutions it's trying and failing for the graphic.

ed: Don't be editing menu.lst unless you're very sure what you're doing. You can really bork things there. 

Esc before grub loads. e edit, you should see a list of boot options. HD0,0 something on the first line, installed kernels after that.
Arrow down to the first kernel. e edit. Backspace to remove splash and quiet. Enter. Arrow back up to the first line. Enter.

---

### Post by wpshooter on 2007-12-05
> **NT4usB said:**
> So, all were dealing with is the annoying out of range error during boot. I just ignore it. 
There's tons of discussions and fixes posted if you want to mess with it. [posts]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+gutsy+usplash+%22out+of+range%22&btnG=Search")
Don't run dpkg-reconfigure, that's only for when your xserver won't start at all...
I've only used it once since I do all my x fixing by editing xorg.conf direct. The -phigh makes dpkg skip most of the questions, iirc.

If you Ctrl+Alt+F1 while you're seeing the out of range error, you'll see in the terminal the display resolutions it's trying and failing for the graphic.

ed: Don't be editing menu.lst unless you're very sure what you're doing. You can really bork things there. 

Esc before grub loads. e edit, you should see a list of boot options. HD0,0 something on the first line, installed kernels after that.
Arrow down to the first kernel. e edit. Backspace to remove splash and quiet. Enter. Arrow back up to the first line. Enter.

The very first post enabled me to get rid of the "out of range" message as the machine is restarting/shutting down by editing the usplash resolution down to 1024/768.  

But I still get the "out of range" message when I am coming **UP** thru the boot process.

What controls the resolution for the usplash during the bootUP process ?

Will look thru some more of the post but thought you might know right of hand.

Thanks.

I found it thanks again.

You have to issue the dpkg-reconfigure command to get the resolution corrected for the bootUP part of the process.

This sure is a lot of reading to fix something like this.  It would be nice if they could fix things like this.  I have been looking for the fix for this over the last 3 days now.

Surely the developers of this O/S should be able to come up with some scheme for having the installation setup/choose a native resolution the would be low enough to cover most any video/monitor specs. that are likely to be used.

Thanks for your help.

---

### Post by oliverb on 2007-12-08
Funny thing is I've seen variations on this behavior with some liveCD distributions too. I wonder if there's some quirk of a number of LCD monitors that makes them return at least one mode that they are completely incapable of supporting?

Anyway I'd like to thank whoever posted the link, I'm still struggling to find clear info on this so could it be condensed into a FAQ entry or sticky somewhere?

---

