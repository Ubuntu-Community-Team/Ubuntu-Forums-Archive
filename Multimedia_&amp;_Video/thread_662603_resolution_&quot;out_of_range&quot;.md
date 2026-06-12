---
title: "resolution &quot;out of range&quot;"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by pat_can_vault on 2008-01-09
I have seen a few similar posts, but still don't get it.

In a few other threads, it has said that by installing some drivers (or whatever) you can get beryl to work more fluently. I hadn't installed the video drivers. So, in the setup it said to extract the files to the /tmp directory. I did. It didn't make any difference, so I figured it wouldn't do any harm.

I restarted the computer, and after logging in, was greeted with the message "Signal is out of range" then a bunch of numbers.

I restarted again, (and then again I think) and then it magically came up. I checked the drivers, and it said that my screen resolution wasn't available as it was before. Groaning, I changed it back to the old intel driver, set it to the correct resolution and worked on the computer for a while. I had decided to completely remove windows, and thought i'd log onto here to find out how to do it, but was greeted with the same message again: "Signal is out of range" then a bunch of numbers.

I'm writing this on windows btw.

I think the driver i tried to install was VGA but I can't exactly remember. It may also have been an Intel 945 or something.

Help, Please?

I love ubuntu! I don't want to have this trouble.

P.S. I am a noob, so if you give any instructions, explain them in detail!
Thanks in advance
pat

---

### Post by renzokuken on 2008-01-09
just extracting driver files to the temp wont work. you need to extract them then "install" them.

what grafix chipset/card do you have?

---

### Post by pat_can_vault on 2008-01-09
Being the impatient person I am, I read through only half of the installation instructions instructions in the manual before continuing with the rest (I should have explained this more carefully) And further on down the page it said it was only available in SuSe (Well, instructions were for SuSe anyway). The instructions given for SuSe in the disc say:

1.  Install Linux
2.  Log in as root or as a superuser
3.  Use a terminal to extract the downloaded files:
        
	a.  tar ÌÔxvf Intel-3.4.3006-20051209.i386.tar.gz

1. Run SuSE's own configurator called 'YAST' 
under System from SuSE application broswer menu
	a. Select the 'Hardware' icon
	b. Select the 'Graphics Card and Monitor' icon
	c. Select 'Grapihcs desktop environment'radio button
	d. Select 'Change'
	e. Under 'Desktop' select 'Graphics Card'
	f. Select 'Add new card'
	g. Under 'General' tab, select 'Intel' and then '945G'
	h. Accept all changes and exit 'YAST'
3. Log out of root or superuser
4. startx

(I did what seemed similar to this under System>Administration>Screens&Graphics!
The driver on the disc is a  "VGA Intel 3.4.3006-20051209"
BUT! I'm not neccesarily trying to install it! I just want my screen back!

---

### Post by manimal347 on 2008-01-09
I945? You shouldn't need to install drivers, as Intel was nice enough to release both the 2D and 3D source code needed to operate their GPU's under a permissive license. Hence, OpenGL (3D acceleration) should come by default on your computer AFAIK, this driver is the very best you can get for your GPU under Linux

 It seems you  have -undone- what UIbuntu set up for you, so try running "dpkg-reconfigure xserver-xorg" from a root terminal (EX: sudo, su) with xwindows and your display manager (GDM?) killed. This reconfigures your xserver (xorg). You can find out how to do this by Googling something like "kill gdm" if it's running. Once you've done this, let the dpkg-reconfigure method guide you through reconfiguring your /etc/X11/xorg.conf file. The critical things are your driver (look up the right one FIRST,) and your monitor sync rates (mainly if you have a CRT monitor- a wrong resolution will cause endless scrolling and can even *DESTROY* 640x480-maximum units). The out of range message likely means you're trying to execute a resolution beyond the ability of your video solution, though don't hold me to that. Alternately, fixing this error -may- be possible simply by editing your current specified driver in your /ext/X11/xorg.conf file (use nano, it's easiest) with the name of the correct one. You'll need root to do this. Whatever you do, backup your Xorg config file first by using the "cp" command to make another copy under a different name. Ex: "sudo cp xorg.conf xorg.bak" assuming you are in the /etc/X11 directory.

You've never made it clear if Ubuntu is dumping you straight into xwindows (and failing miserably), or if you can get to a console. If you cannot, try hitting ctrl-alt-F2, and try ctrl-alt-bkspace. If that fails, use the recovery function on your Ubuntu live CD, or if you don't have a live CD, any mainstream live Linux CD will work as long as it supports mounting ext3 partitions (unless you formatted as something else...). You may have to mount your ext3 partition (your main Linux one) by hand using the CLI "mount command." As I've never seen your computer, all I can tell you there is to read the relevant man pages. 

You're gonna want console Web access to help you in fixing your xserver (xorg), so run "apt-get install elinks" as root when you want to consult Web resources in Linux. installing "bitchx" for IRC -based support may also prove useful. Read the man pages if these programs confuse you. You can do that with "man 'progname.'"

Also, nothing but black magic or a complete code rewrite could make Beryl run well; at least according to the experiences of people I trust. Re-evaluating how essential eye candy is to you might prove wise.

I apologize if this was obtuse. If anything confuses you, either Google it, ask about it, or read the relevant man pages. As a last word of advice, in the future, try to do things the "Ubuntu Way" first, such as using the package manager (synaptic, aptitude, apt-get, .etc) or native Ubuntu (NOT Debian .DEB's instead of "alien" .RPM files, and loading graphics drivers and w-fi cards through the restricted driver manager, if installed. Also, executing "dmesg," which shows you the output of the Linux kernel, may aid you in troubleshooting this and other problems.

---

### Post by pat_can_vault on 2008-01-09
> **manimal347 said:**
> 
I apologize if this was obtuse. 


Nothing to worry about!:KS
Thankyou very much!
This was very helpful!

Earlier today I tried overwriting the xorg.conf file with the one from the LiveCD, but that didnt work.  

I will try out the above methods. 

pat

---

