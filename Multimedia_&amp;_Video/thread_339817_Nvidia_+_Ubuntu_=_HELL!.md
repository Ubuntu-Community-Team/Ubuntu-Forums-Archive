---
title: "Nvidia + Ubuntu = HELL!"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by RaZoR-x11 on 2007-01-16
Hey there,

Where do i start with this, mmmm i think il start with nvidia display driver which are complete load off balls, Before xmas 2006 i was running debain which if some dont know is the daddy to ubuntu, and i have the 7xxx driver working lovly, now that it came close to the new year i though to myself new year umm try something new hey? so i did i downloaded the Ubuntu Edgy 6.10 live cd, install it boom it was done now, the next day i went to install the driver and you guess it it didn't work and ive tryed it 1000's off time with diffrent kernel's, libs, blacklisting the horrable frame buffer's, and alot off other stuff,
now the thing i dont get is if Ubuntu was built on Debain then why in god know's dosen't the nvidia driver's work tryed Envy, all the tutorials on the net for install nvidia, BUT! none work.

Please help this is becoming areal pain in the arse.


Thank's in advnace.
RaZoR

---

### Post by Sqwishy on 2007-01-16
What have you been sniffing?
Actauly in my experince Nvidia + Ubuntu = Very HAPPY!
Although it somewhat depends on the driver and you're card, what card are you using?

---

### Post by deadgobby on 2007-01-16
Have you seen this link yet??
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Gobby

---

### Post by tseliot on 2007-01-16
> **deadgobby said:**
> Have you seen this link yet??
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Gobby

Try point 4 of the Problems Section of that guide

---

### Post by RaZoR-x11 on 2007-01-16
Thank's the quick reply,

Yes as i said i have try'd the link above nothing seem's to work.
My card is a Nvidia 5200fx 128mb,
but i have a spare Radeon 9250,
would it be better to use the Radeon?

P.S I have not bin sniffing nothing i thank you very much.:)

---

### Post by hal10000 on 2007-01-16
I have downloaded and installed the latest drivers from nvidias site and it works with no errors. (much better than the ubuntu provided driver).
But you have to be sure that some packages are installed on your system: [COLOR="Red"]build-essential, kernel-headers, binutils, pkg-config xserver-xorg-dev[/COLOR]. To install the driver you have to shutdown your xserver and run the script from the command line (with sudo).

EDIT: Here is a howto:[http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+driver+build](http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+driver+build)

---

### Post by RaZoR-x11 on 2007-01-16
Thank you hal, but i have them all i have rebuilt the kernel several time's 
and i still cant get it working. 

i have got these kernel's installed.

 ```
"2.6.17-10-386" && "2.6.17-10-genetic" && "2.4.27-2-386"
```

---

### Post by deadgobby on 2007-01-16
> **RaZoR-x11 said:**
> Thank's the quick reply,

Yes as i said i have try'd the link above nothing seem's to work.
My card is a Nvidia 5200fx 128mb,
but i have a spare Radeon 9250,
would it be better to use the Radeon?

P.S I have not bin sniffing nothing i thank you very much.:)
 Umm stupid question here, but do you have both vid cards in your PC? I hope you don't. That would only confuse the O/S and the BIOS. If not, then try the Rad and here is a link
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Gobby

---

### Post by RaZoR-x11 on 2007-01-16
Lol, no i would not dream off putting a agp card in a pci.;)
motherbord is a: 

```
ASUS K7VT4A+
``` 

umm to card's in it i dont think so but thank's ;)

---

### Post by raul_ on 2007-01-16
Conclusion: Nvidia sucks

---

### Post by mrunion on 2007-01-16
Well, YMMV (obviously) but ATI is MUCH worse than nVidia on Linux in my experience.  Why do you need the LATEST drivers for that card?  Can't you just install from the Repository?  I've got absolutely no problem with my nVidia card and I installed from the repository (v. 8776 I think).  I have a laptop with a 7400 card in it.

Anyway, I hope you get it sorted.

---

### Post by RaZoR-x11 on 2007-01-16
I should have added that the driver's do work but when booted into the gui at the login the slash screen comes up and load's window's manager and then the screen stays black with the white cursor, cursor can move around the screen but no gui at all.

---

### Post by hal10000 on 2007-01-16
I had to install the LATEST driver because googleearth would not do it with any other.

---

### Post by RaZoR-x11 on 2007-01-16
Well, i have tryed the latest driver etc... and they boot up with the lovly nvidia logo at stop at splash screen after login, starting to wonder if i can get the
"NV" driver to work as well as the official one's because i have not got a problem with "NV" native driver's.

](*,)

---

### Post by hal10000 on 2007-01-17
Have you looked into the file /var/log/Xorg.0.log to see if there are some parts of your older 7xxx driver hanging around?

I had this problem a few months ago.

---

### Post by steevc on 2007-01-17
I had my own Nvidia hell last night. I've been using the on-board Nvidia graphics on my old motherboard, but just got a 64MB MX400 in a swap that I would hope might give some improvement in performance. I previously tried an MX4000, but the MB would not detect it.

I get a display from the card and see the NVidia splash screen before getting the KDE log-in. The results from there on have varied. I have managed to log in a couple of times, but the system was not too stable and some apps would not start.

I tried various settings using

dpkg-reconfigure xserver-xorg

When I gave up I was just getting a blank screen and the system seemed to be locked.

I will have a go with the instructions linked from this thread tonight. Will I need the legacy version for the MX400?

---

### Post by RaZoR-x11 on 2007-01-17
Hey,

Well i have a mx400 somewhere lol, but if you want it to be as stable use the nv driver.

Boot into recovery, then after loaded  type:

```
nano /etc/X11/xorg.conf 
```

Then the line that says nvidia change that to nv, thensave the file by:

```
Ctrl + O
```

then use:
```
shutdown -r now
```

after reboot should work :D

---

### Post by hal10000 on 2007-01-17
If you want your nvidia 3d Harware accel you may follow this thread:

[http://ubuntuforums.org/showthread.php?p=2024864#post2024864](http://ubuntuforums.org/showthread.php?p=2024864#post2024864)

scroll down to kvonb 's posting and follow the steps he advises. I'm sure this will solve your nvidia problem.

---

### Post by steevc on 2007-01-17
> **RaZoR-x11 said:**
> Hey,
Well i have a mx400 somewhere lol, but if you want it to be as stable use the nv driver.


Is nv the free/open driver? I tried selecting that in the xorg, but didn't get anywhere. I'd like to get some graphics acceleration for the odd game of Planet Penguin Racer.

I don't really need a whole new PC, so I'm just trying to get the best from what I have already and any bits I can scrounge. I just boosted the memory as well. Next on my list is a better CPU. The board will do up to an Athlon XP 2600.

Update: Just been looking at the nvidia documentation [http://doc.gwos.org/index.php/Nvidia]("http://doc.gwos.org/index.php/Nvidia"). I think I'll try uninstalling the drivers I have then install the legacy drivers.

---

### Post by Xemanth on 2007-01-17
nvdia + ubuntu is lovely combination. I have never had problem with nvidia linux drivers.

ATI's fglrx package is ](*,)

---

### Post by dabl on 2007-01-17
Yep -- what Xemanth said.  My first impulse after trying Kubuntu on an ATI card, and reading the instruction on how to patch up fglrx, was to give it up and plan to live with Windows.  I'm glad I didn't -- the better solution was to buy an Nvidia card.  I'm very pleased with the performance of my Kubuntu system, including Beryl, on my GeF 7900 GS.

---

### Post by steevc on 2007-01-17
I wondered what a 7900 GS might be. This site 

[http://www.gpureview.com/show_cards.php?card1=117&card2=443]("http://www.gpureview.com/show_cards.php?card1=117&card2=443")

gives some idea of the scale of difference in performance between various cards. About x20 in this case.

I used to have some idea of what was state of the art in graphics cards a few years back, but I just don't keep up with it these days. I find it more relaxing to be content with what I have until I have a real need for more performance or can upgrade for a nominal amount.

---

### Post by sanderjd on 2007-01-17
I've found the easiest way to install nvidia drivers is to use automatix ([www.getautomatix.com)](www.getautomatix.com)). I still had to manually change my resolution in /etc/X11/xorg.conf, but hey, I've *never* found a good way to change resolution, so this is nothing new.

---

### Post by RaZoR-x11 on 2007-01-17
Hey, 

thank's [sanderjd]("http://www.ubuntuforums.org/member.php?u=97670") the automatrix worked, now im stuck at the first problem i had, dam GLX!

```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000040gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
```

im really starting to think nvidia and this pc will never work.:-|

---

### Post by steevc on 2007-01-17
I've just installed the nvidia-glx-legacy and done a restart. Trying to do startx gets me a message about ksmserver not being started before dropping me back to the console. The console that has a load of messages about not being able to open /dev/wacom or init various font path elements.

Any ideas?

Update: I saw it was complaining about Composite not being allowed, but found the nvidia-xconfig option to fix that. Now I still see an error in the log about opening the security policy file /usr/lib/xserver/SecurityPolicy. That folder doesn't exist.

---

### Post by hal10000 on 2007-01-17
I'm almost sure that all your problema are caused to the simple fact that you are using a version of nvidia-glx that is not compatilbe with your current installed nvidia module.

So if you want 3d hardware acceleration follow this guide, it's very very simple if you FOLLOW THE STEPS described, you just need to copy'n paste most of the commands:
[http://ubuntuforums.org/showthread.php?t=336412&highlight=1.0-9746](http://ubuntuforums.org/showthread.php?t=336412&highlight=1.0-9746)

EDIT: this posing was mainly dedicated to RaZoR-x11

---

### Post by steevc on 2007-01-17
I don't think it can be a driver issue as I somehow just managed to get back into KDE. It's still not quite right as I first just got a console on the desktop with no title bar. I tried running kicker and managed to get all my apps running. I need to try a restart and see if it comes back.

I did a couple of tests using glxgears and Planet Penguin. The former showed 240fps which I don't think is better than the on-board graphics. PP Racer runs at 40-50fps, which is adequate, if not exceptional.

I'll play with it for a while and see how it goes.

Cheers

Update: I've obviously messed something up in KDE. After a restart I got the bare desktop again. Running kicker for me the task bar at the bottom, but no window title bars. I've no idea how to start on fixing that. I ran out of time to investigate further last night. I have to get at least some sleep ;)

---

### Post by RaZoR-x11 on 2007-01-18
Lol, i think it's a big pain in the arse not bin able to play any game's tryed xmoto,trigger,etc they all worked fine but after like 5min's off play system halted/crashed, had to do a nice hard reboot. but il have a nother look at the pc today, think il just format the whole dam thing im getting so dam pissed with it.
](*,)

Edit: i Forgot to add that last night after i found that when you remove the Nvidia-Glx driver it still leave's files behind, and wondering if the framebuffer has anything to do with it "RIVAFB" + Nvidia = ?


Cheer's lee.

---

### Post by RaZoR-x11 on 2007-01-18
Deleted.

---

### Post by RaZoR-x11 on 2007-01-18
[

---

### Post by NoobieDoobieDo on 2007-06-26
NVIDIA + Ubuntu Feist (or) + Ubuntu Edgy = total crap.

I've been working for over 6 hours to get my Ti4200 to "act right".  GNOME loads but everything is SLOW.  Resizing / maximizing / minimizing = SLOW.

This is total crap, I've read over 50+ threads on this issue with NO RESOLUTION.

---

