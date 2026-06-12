---
title: "Can not get resolution 1680x1050"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by Zayne on 2008-03-04
So.. this is my first time posting. Hello!

And here goes..

I'm a brand new Ubuntu user. Running 7.10, installed two days ago. Been a windows user all my life, and simply too lazy to explore my alternatives until upon getting a new computer, Vista really managed to tick me off. Anyway..i'm getting off my subject.

I got my video card working, after several hours of severe confusion I managed to get it functioning 3D and all. 

But my native resolution, and the one I was using on Vista (1680x1050) isn't there. It plain doesn't show up at all in my list of resolutions. There's a few higher, but using them cause my monitor to turn itself off and on repeatedly and the system refuses to respond so i'm pressed to force my system to shut down. That's definitely a no go.

My monitor is a Dell E228WFP Widescreen, 22". My video card is an ATI Radeon 2600 XT.

As I said earlier, i'm a new user. Totally green. So my plea is.. I need somebody patient enough to put everything in simpleton's terms for me. Step by step instructions if possible. All I want is to get 1680x1050 back. 1440x900 is all I can run right now..and gosh it's an eyesore on this screen, especially for a graphic designer.

I'll be forever grateful for any assisstance. And will provide any information I can as long as I can figure out how to..haha.

Thank you in advance!

---

### Post by sloggerkhan on 2008-03-04
As a linux newb, it really sucks to have a newer ATI card.
You'll soon find that every month there is a new driver release, and you're stuck in a sort of eternal beta test. Eventually, as your card ages the open source driver will have caught up enough that you can use it and step out of the endless driver cycle.

That said, I'd go ahead with trying out the latest ATI fglrx driver.
Here's how I'd go about doing it:
1. go to AMD's website and download the latest driver.
2. purge the current ATI fglrx driver using synaptic.
3. sudo dpkg-reconfigure xserver-xorg from the command line
4. run through everything and select vesa driver
5. go to the directory you downloaded new driver
6. in terminal of that directory run ./<name of driver installer> --buildpkg ubuntu/gutsy
7. That terminal should then produce several *.deb files in the same directory as the installer.
8. Install those debs.
9. sudo dpkg-reconfigure xserver-xorg, this time choose fglrx driver
10. sudo aticonfig --initial from the command line

11. reboot (needed because of new kernel module)


see if things worked.


Possibly you might need to do this as step 10.5:
10.5. gksudo gedit /etc/x11/xorg.conf and add 
```

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "GLcore"
EndSection

``` as the modules section. 

There may be slight changes to take at different steps in this process depending on how things go for you, but that's the general outline of it.

For more info, try a forum search.

Also, if there is an error at any point in the process, be sure to post it so we can tell you what to do.
Lastly, if something goes wrong during this process, you could be dropped to a CLI without gui.

---

### Post by Zayne on 2008-03-04
Wow, thanks for the quick reply!

My head is spinning a little bit though. 

Before I try this, I better clarify a few things:

Upon going to ATI's website, do I download the WINDOWS driver? Or is there a version for Ubuntu?

What on earth is a deb, and how do I install it? Is there a command for this or is it a double-click?

To get my video card working initially, I was directed to use a program called Envy by somebody on IRC. I'm assuming i'm to abandon that method all together?


Thank you again.

---

### Post by sloggerkhan on 2008-03-04
you could try envy. In theory,  Envy is a script that does something much like what I listed above. I've never used it, it used to be only for nvidia cards.

At AMD's website, you want to get the linux driver.
From here:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
Linux, or Linux x64 for your card.

A deb is the standard installer file for debian distros, or for Ubuntu. they are files install similar to .exe or .msi files on windows. When you go to synaptic or the add/remove menu, .deb files are what's being dealt with. You need to use .deb files for the install to be seen by your package manager. You can install them by double clicking. (try getdeb.net, if interested in seeing a deb file.)

---

### Post by Zayne on 2008-03-04
Thing is, Envy worked, but..

Okay well I just logged off because something went very odd with all of my windows, their top bars all vanished. Couldn't move nor close anything anymore. So I logged out and back in. Now my video card is doing nothing but standard graphics. It won't do anything 3D anymore. And all I did was log out..hmm.


Envy also didn't give me the resolution I want. =[

So, i'll try this now, cross my fingers and hope it works (and that I don't screw it up).

I'll post and let you know how it goes.

---

### Post by Zayne on 2008-03-04
On step six, upon entering this:

./ati-driver-installer.run --buildpkg ubuntu/gutsy

I get this:

bash: ./ati-driver-installer.run: No such file or directory

I'm assuming i'm doing it wrong. =[ I feel so stupid.

---

### Post by Zayne on 2008-03-04
Really sorry, I know it's awful to triple post but i'm a little desperate. Sigh.

I missed the version on the file before, so I corrected that. But it still gave the same error. So I moved it to desktop and tried from there. 

./ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy


This time it yielded this error:
bash: ./ati-driver-installer-8-02-x86.x86_64.run: Permission denied


..I'm so confused.

EDIT: Wow. Well, my problem is solved.

As a last resort, I attempted using Envy again. I installed the ATI drivers using Envy and rebooted and my resolution was now selectable. I'm guessing it was to do with using sudo dpkg-reconfigure xserver-xorg. The first time I used it I selected 'ati' instead of 'vesa'. I'm not sure if that's the fixing factor but it's the only thing I did differently.

Thanks so much for pointing me in the right direction!

---

### Post by sloggerkhan on 2008-03-04
okay, several things here, lol, though I'm glad it worked for you.
To run the installer, you probably needed to right click it and select 'allow executing file as program' under the permissions tab. Once it can run, in the terminal you should have been able to type ./ati and then hit tab and have it autocomplete to the full name.

2nd of all, ati is the general open source ati driver, vesa is a really basic driver, and fglrx is the proprietary ati driver, which can be kind of confusing. My instructions where from the perspective of purging a previous fglrx install, which sounds like it might not have been where you were at, and may have even confused the issue. Sorry!

In any case, I'm glad things worked out for you.

the fglrx driver isn't exactly the most user friendly thing for a new user to encounter, especially if you have a newer ati card.

---

