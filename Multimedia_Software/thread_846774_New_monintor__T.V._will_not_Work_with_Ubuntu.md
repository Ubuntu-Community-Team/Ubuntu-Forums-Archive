---
title: "New monintor / T.V. will not Work with Ubuntu"
date: 2008-07-01
forum: Multimedia Software
---

### Post by Sabar on 2008-07-01
Hello Every one. I just bought a T.V. to use as a monitor on my computer. The bad part is it's only working if I boot up windows. 

     I have an ATI video card, this thing is a 32" HD Wide screen T.V. Is there any way to boot up in some kind of safe mode and change something so I can use my Ubuntu again? 

     Oh Yea maximum Resolution is 1366x768, and it is made by Go Video, what it is is doing I get the grub page then when Ubuntu should be loading it goes to a blue screen and says no signal I dont know what other information to give let me know if you need to know something else. 

Thanks 
Sabar

---

### Post by s60mjk23 on 2008-07-01
go to your system button, then preferences, then screen resolution. it will detect it and then click apply, or set it up yourself.

---

### Post by Rhubarb on 2008-07-01
Press Alt + F2:
```
gksu displayconfig-gtk
```

In the screen tab, Press the Model button.
Try Manufacturer: Generic
Model: LCD Panel 1360x768

It's not 1366x768, but it's only 6 pixels off, which should be close enough.
Then log out, and log back in again and your resolution should be correct.

---

### Post by Sabar on 2008-07-02
How do I do these things if I have no picture on my screen? the only thing I have is a blue screen and a bar that says no signal. 

I can hook up the old monitor but I was thought if I did that then what ever I did to fix the new one would screw up the old one.

Sabar

---

### Post by aeiah on 2008-07-02
find out what resolutions your tv supports. is this via vga, dvi or hdmi?

it will most likely support 1024x768 (as well as better ones). if it does, plug in your old monitor and set your res to this, and then reboot with your new tv plugged in instead. it should display in the stretched and somewhat ugly 1024x768 resolution. from there, you can tweak it to your desired resolution.

---

### Post by Sabar on 2008-07-02
sounds like a plan. I just didn't know if there was a way to fix it while this monitor was running. I'll see if that works.

Oh yea it has VGA plug ins. all I did was take the VGA off my other monitor and put it on this one.

If I do go and buy another video card ( thinking I can find one that will run this better) what is best supported by Linux? or where is the best place to post that question?

Thanks
Sabar

---

### Post by feenicks on 2008-07-02
I just resolved a nearly identical problem.  Unless your ATI card is really old, you don't need a new one.  I'm still a noob at Linux, so this is just my experience here.

When you get the blue "No Signal" screen, type Alt+F2 (maybe CTRL+ALT+F2, help me out guys) to get the command prompt.  Then run this:
sudo dpkg-reconfigure xserver-xorg
and enter your password.

This runs a utility to reconfigure your xorg.conf file.  I used the default values for the most part.  I think I set the screen resolution at 1280x1050 or 800x600 the first time.  There probably will not be a 1366x768 so just pick whatever.  Your problem is with the screen resolutions or monitor settings.  You don't need to change anything regarding keyboard and mouse set up so leave those on autodetected defaults.  Anyway, the default values all the way through *should* get your screen to work.

Chances are when you do get it working it won't be very pretty.  You may need to install a better ATI driver, which I can't help you with since I used Nvidia here.  Just search the forums.  Start here:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

Once you get the drivers installed you still might not have full widescreen resolutions.  I wrestled with my set up forever before finding this:
[http://ubuntuforums.org/showthread.php?t=96980](http://ubuntuforums.org/showthread.php?t=96980)

Post #28 worked for me big time.  Don't forget to backup xorg.conf before you change it manually.  And back it up again once you get it perfect.

---

### Post by xc3RnbFO8P on 2008-07-02
I just want to add this about HD:
[http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html]("http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html")

---

### Post by Sabar on 2008-07-15
To add salt to the wound for some reason my regular monitor  (17") seems to have gave up the ghost on me. I have no idea whats wrong with that but it isn't working with Linux or Windows.  In fact when I turn it on, even pressing the menu button gives me nothing. So I am kinda stuck working this problem with the big monitor  for now.


Ok. So please let me get this straight. If I 

1. start the computer.
2. under the grub start up under "recovery"
3. Type in > gksu displayconfig-gtk

Will I get a graphical box with options?  Type it exactly as above?

If instead I type in 

> sudo dpkg-reconfigure xserver-xorg

Will I get a graphical box? or more words? 

Does anybody have an opinion which idea is the best one?

My ATI card is now three years old. should I be looking to replace it with a new NVidea Card now?

---

### Post by Sabar on 2008-07-15
Ok. here is what I have done so far.

Under the grub I clicked on "Recovery"

then I typed in > Sudo dpkg_reconfigure-phigh xorg-xserver

The response. I got was it did not recognize this

So then I typed in > sudo dpkg-reconfigure xserver-xorg This got me a box with options I followed thruethe options, set my monitor at 1024x768 clicked on the option so say it was bigger than 24"  and basically defaulted to everything else.

Didn't work. still just have the no signal screen.
same as I had before just the grub screen then the load screen with the bar on it then .......... nothing ....

I was about to try the third option to see if that does anything. but I wanted to post this to see if there was something under advanced options I should have done.

Thanks by the way, to every one trying to help me out



P.S.   

I Ran > gksudo displayconfig-gtx

The responce I got was " GTK - WARNING ** cannot open display

I also reran > sudo dpkg-reconfigure xserver-xorg 

the only diferance was I tried the highest first number that ended with a x768  I think it was 12??x768. then I went under medium and chose 1024x768

same result of "No Signal" 

I did find this interesting post though. I just didn't find anything in it that helps yet though. [[COLOR="Blue"]Comprehensive Multimedia & Video How-to [/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683&highlight=ati+drivers")

If anybody has any more ideas or sees what I am doing wrong please let me know becouse my wife is getting really mad at me. 

Thanks

---

