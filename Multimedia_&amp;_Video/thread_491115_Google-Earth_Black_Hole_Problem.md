---
title: "Google-Earth Black Hole Problem"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by i8bugs on 2007-07-03
I got everything working including my scanner, but there is this one remaining issue.  I still have the google-earth black hole problem that some people have using Nvidia drivers.  Now I have looked in all the forums and as a result, I installed ENVY, and let ENVY install the latest drivers.  This solved the issue for some, but not for me.  Some games do not run either, for example NEVERBALL and NEVERPUTT do the same thing.  I uploaded screeshots to show what I'm experiencing.

I had all these things working in Edgy, but I'm running Feisty now, and that is when these stopped working.  I trued uninstalling and reinstalling.  I tried installing from the website and not thru Automatix.  The result is the same no matter what.

I didn't see a SOLVED thread for this issue.  Can someone point me in the right direction?
Here are some outputs:

i8bugs@i8bugs-desktop:~$ lspci -n | grep 0300
02:00.0 0300: 10de:01f0 (rev a3)
i8bugs@i8bugs-desktop:~$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)


i8bugs

---

### Post by compiledkernel on 2007-07-03
Hmmmm, 3d driver reinstall maybe?

---

### Post by joselin on 2007-07-03
Are you running beryl or compiz?... if yes, disable it and then launch google earth.

---

### Post by i8bugs on 2007-07-03
Can you expand on that a little? The extent of my knowledge for drivers was installing ENVY and letting it do its job.  I did the 3d rendering check and the reply was yes.

I have the same system as before when it did work so there should not be a hardware issue.  Where can I get new 3d drivers?

EDIT:  No beryl or compiz.

---

### Post by i8bugs on 2007-07-03
Just trying to get this figured out, and get it back on the front page.

---

### Post by weblordpepe on 2007-07-03
I know this is unrelated & won't help you in any way - but damn dude your window theme & icons look good. What are they?
BTW it looks like google earth before its loaded textures from the internet. (Thats my lousy attempt at helping)

---

### Post by david_2001 on 2007-07-03
What version of the "latest" nvidia driver did you install?  According to the nvidia [COLOR="DarkOrange"][readme]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html")[/COLOR], the GeForce4 MX Integrated GPU 	(0x01F0) is only supported by the legacy 1.0-96xx driver.

---

### Post by RomeReactor on 2007-07-03
Hi. Just dropping by to mention that people over at [Google Groups]("http://groups.google.com/group/earth-linux/browse_thread/thread/26ea67e8bc868a59/0c34157535d114f8?lnk=raot") have been having the same problem; one poster suggests that the problem has only come up since the more recent nVidia drivers incorporated ARGB Visual extensions, and another one points out that going to full screen (by pressing **F11**) all the images show up, although it's too slow to use.

---

### Post by i8bugs on 2007-07-03
On the theme, I'm using NASA night launch for the firefox browser, and "black plastic" theme for the windows, with "crux" controls.  I did thesemi transparent thing with the toolbar, and the wallpaper is a fly agaric mushroom  (attached) that I took in my front yard.

Using F11 did nothing to help in this case  How do I get and install the legacy 1.0-96xx driver?  I'll surf for the howto unless someone can find a link first.
i8bugs

---

### Post by david_2001 on 2007-07-03
> **i8bugs said:**
> Using F11 did nothing to help in this case  How do I get and install the legacy 1.0-96xx driver?  I'll surf for the howto unless someone can find a link first.
i8bugs

If you're already up to installing drivers from the nvidia website then just get it from [http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html).

---

### Post by i8bugs on 2007-07-03
When I go to install the driver I get:

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

Tried to find the command to stop X server.  I'm not a coder, so I don't know the command. Anyone?
bugs

---

### Post by compiledkernel on 2007-07-03
sudo /etc/init.c/gdm stop 

thatll take you to a command prompt, then youll have to reinstall the driver.

---

### Post by i8bugs on 2007-07-03
Crud!  This is what I got:

root@i8bugs-desktop:/home/i8bugs# /etc/init.c/gdm stop
bash: /etc/init.c/gdm: No such file or directory

i8bugs

---

### Post by compiledkernel on 2007-07-03
oops, mah bad. 

sudo /etc/init.d/gdm stop 

the c was a mistype. 

Sorry.

---

### Post by i8bugs on 2007-07-03
compiledkernel,
OK, that didn't work out.  When I executed that command, it went to what looked like a command prompt screen, but would not respond to input...basically dead.  When I did a ctrl+alt+del to reboot, I lost my network, and my network icon.  Very weird!  Had to reboot again.  Icon stayed gone, but I got my network back.

Well, this is turning into an all day thing.  This is worse than the scanner!  Hey, we tried!

I have the file, I just can't find a way to install it without probs.  I'd kinda like to get GE going though...bothers me to have something that is inop.

i8bugs.

---

### Post by i8bugs on 2007-07-03
Hey quick question, can you recommend a decent graphics card that is linux-ubuntu friendly?  I may just update.  I'm not a gamer, so I don't need a big potato masher, just something dependable.  That may be easier than wrecking my system to get GE to work!
i8bugs

---

### Post by weblordpepe on 2007-07-04
Any nVidia geforce card after a geforce 3. At least I think. nVidia are very good with linux but the older cards arent supported (as someone mentioned about your MX)
Check out a Geforce FX or 6xxx or 7xxx or 8xxx. Even the low end versions of those cards will be great. They'll be modern chipsets even if they arent super FPSwhores.

---

### Post by i8bugs on 2007-07-04
> **compiledkernel said:**
> oops, mah bad. 

sudo /etc/init.d/gdm stop 

the c was a mistype. 

Sorry.

Ok, I tried this and it did not get me to a command prompt.  I tried logging in with the gnome failsafe session thinking that would get me there, and I still got the xserver warning.  Next, I tried hitting escape during boot up and tried logging in with ubuntu safemode.  I got close, as it started to unpack, I got a different warning, that I was working in runlevel 1 and that I needed to be in runlevel 3.

Shouldn't it be simpler than this? What is going wrong?
i8bugs

---

### Post by weblordpepe on 2007-07-04
News just in.
The earth is covered in a gigantic layer of black goo. Google have responded by updating the Google earth images accordingly.

Actually.
When you go to boot into Ubuntu or Windows (the GRUB screen) there should be an option for recovery mode or something. it'll prompt you for the root password halfway through the boot process.

---

