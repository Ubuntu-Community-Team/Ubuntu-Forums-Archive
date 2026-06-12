---
title: "skype video issue"
date: 2009-09-14
forum: Multimedia Software
---

### Post by VOLKOV9 on 2009-09-14
Skype audio works fine.  When I try to video connect, they can see me, but I just get a jumbled mess of mostly white with a few random pink lines.  When I try the video test, I hit the "Test" button, and the little black test video screen remains, but the "Test" button itself disappears, becoming a small transparent rectangle (so I see my desktop or firefox or whatever is immediately behind the Options window).  Any guesses on how to fix it?

If this is covered by some other thread, forgive me and please point me to it, but all the threads I can find have other problems with Skype video.

I'm running 8.04 64-bit, btw, and updating to the latest version of Skype had no impact on the problem.

I do recall the video test working fine when I first got Skype back in... June I think... but I don't recall what I've changed since then.

Thanks!

---

### Post by VOLKOV9 on 2009-09-21
*bump*

---

### Post by Conu on 2009-09-22
Dont know if this is your problem sounds a bit like it [html]http://www.cairo-dock.org/bg_topic.php?t=2156&pos=0[/html]

---

### Post by gradinaruvasile on 2009-09-22
Go here:

[http://forum.skype.com/index.php?showtopic=411441](http://forum.skype.com/index.php?showtopic=411441)

Find my post there. It might fix ur problem. Correct the path of the library, its different on 64 bit systems i guess. Also u might need some packages to install.

I think the command for 64 bit is:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

Just copy-pase it in a terminal.

---

### Post by VOLKOV9 on 2009-09-22
Thanks, grad; this looks promising.  However, "locate" finds no "compat.so" file, and no "libv4l" directory.  Synaptic only gets one hit for "libv4l", and it's an extension library for something called "ruby".  searching for "v4l" and "video4linux" get more hits, but all similar things - plugins and extensions for other things to work with v4l, not v4l itself.  One difference is your post says you're running 9.04, and I'm on 8.04 (because 9.04 apparently hates my hard drive).  Any thoughts on why I can't find v4l?

Wikipedia says that v4l is closely tied to the linux kernel, and has been around since much earlier versions of the kernel than mine... and my flash works, so I imagine I have it in some sense, but I can't find it.

---

### Post by VOLKOV9 on 2009-09-24
So, at <http://ubuntuforums.org/showthread.php?p=7987358>, hardy is not listed.  so to what library do you think I should point?  Or maybe this hints that it's a different issue, since I installed the hardy version of Skype.

---

### Post by mcscratch on 2009-10-21
*bump*

---

### Post by tudor117 on 2009-10-25
This is what I did to get it work:
From synaptic install lib32v4l-0
If you installed from skype's website (the new beta) there will be no skype.real but only a skype executable. You need to rename it to skype.real
If you already have a skype.real don't worry about it.
Next, change/create the file skype to ```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype.real 
```Make it executable.
Run skype from terminal. Test webcam.

EDIT: Just realized there's no lib32v4l package in hardy. Sorry, maybe you could try intrepid's package? Actually I doubt you can because it depends on some newer packages. It's worth a try at least.
[http://packages.ubuntu.com/search?keywords=lib32v4l-0](http://packages.ubuntu.com/search?keywords=lib32v4l-0)
On the other hand you could try building it.

---

### Post by oscarmeyer51 on 2009-11-17
Additional solution (not related to cairo or QT?).

For 32-bit Karmic Koala, I found this thread & solution. I have included the preload for the /usr/lib and the /usr/lib32. For me the former works and I assume the latter works for 64 bit (as skype runs in 32 bit).

Thread:  [http://forum.skype.com/index.php?showtopic=411441](http://forum.skype.com/index.php?showtopic=411441)

ig-88 posted the lib32 solution (Part 1) and Part 2 was posted by the_wOndErEr57 and gradinaruvasile (yes, I had to see my solution twice before I realized that lib32 and lib were not the same...<grin>).

Solution:

Part 1 posted was:

i use a "046d:08d9 Logitech, Inc. QuickCam IM/Connect" on ubuntu 9.04 amd64. the webcam just shows garbage while testing and simply shows nothing in calls.

a workaround is to move /usr/bin/skype to /usr/bin/skype.real
install lib32v4l-0 via apt-get and create a new /usr/bin/skype with the following content:
CODE
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real
#################

Part 2 Posted was:

QUOTE (gradinaruvasile @ Fri Aug 28 2009, 17:15)
Go to the original post
I have a
0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam

on Ubuntu 9.04 and it is working only with the ld_preload thingie mentioned before.
BUT the path is incorrect (maybe a distro thing?) the correct command is this one:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

****************

In summary, 
1. sudo mv the /usr/bin/skype binary to /usr/bin/skype.real
2. sudo gedit /usr/bin/skype
   (or your favorite text editor instead of gedit)
3. copy & past into the editor the following

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

4. enter "sudo chmod 755 /usr/bin/skype" without quotes to make the script file executable
5. start skype via the menu and test the video

---

### Post by pickarooney on 2009-11-21
> install lib32v4l-0 via apt-get

What repository is this in (for Jaunty)?

---

### Post by wetinwales on 2009-12-23
SORRY THIS IS IN THE WRONG THREAD.

I am running jaunty 9.04 on a four core amd 64bit with the deb skype 2.1.0.47 installed from skype website. 
I have a Logitech QuickCam Messenger which works good in Cheese.

As you all guessed... I get the green or multicolored hash in the Skype Video test.
Finger accross camera changes colours etc.

I have tried every version of solution I can find in forums - Preload v4l1, renaming of /usr/bin/skype.real etc etc... all to no avail.

I have checked the libs and they all seem to be "newest versions"

I think I am now lost.

Here is terminal output clue?

me@comp:~$ ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

So many posts claim success for various solutions. None for me !!!!

Can anybody help ?  

Thanks

---

### Post by tudor117 on 2009-12-23
Hi wetinwales,

Not sure if you started a new thread. So here's my thought.
Did you install *lib32v4l-0*?
Also check that /usr/lib32/libv4l/v4l1compat.so actually exists.

---

### Post by saltmore on 2009-12-24
This should fix it for you.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

---

### Post by nsa1001 on 2009-12-31
> **oscarmeyer51 said:**
> Additional solution (not related to cairo or QT?).

For 32-bit Karmic Koala, I found this thread & solution. I have included the preload for the /usr/lib and the /usr/lib32. For me the former works and I assume the latter works for 64 bit (as skype runs in 32 bit).

1. sudo mv the /usr/bin/skype binary to /usr/bin/skype.real
2. sudo gedit /usr/bin/skype
   (or your favorite text editor instead of gedit)
3. copy & past into the editor the following

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

4. enter "sudo chmod 755 /usr/bin/skype" without quotes to make the script file executable
5. start skype via the menu and test the video

NB for 64 bit, step 3 needs to be modified as follows:

3. copy & past into the editor the following

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

Good luck!

---

### Post by taps on 2010-01-04
> **oscarmeyer51 said:**
> 

In summary, 
1. sudo mv the /usr/bin/skype binary to /usr/bin/skype.real
2. sudo gedit /usr/bin/skype
   (or your favorite text editor instead of gedit)
3. copy & past into the editor the following

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

4. enter "sudo chmod 755 /usr/bin/skype" without quotes to make the script file executable
5. start skype via the menu and test the video

This worked for me (32-bit Karmic). Thank you! :)

---

### Post by Muttley99 on 2010-01-22
> **saltmore said:**
> This should fix it for you.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

thank you saltmore! fixed my problem with skype video!

---

### Post by towheedm on 2010-01-23
> **taps said:**
> This worked for me (32-bit Karmic). Thank you! :)
Worked for me also.  Karmic 32bit + Eyetoy (Finally got the mic to work with PA).

---

### Post by angliski on 2010-01-26
Sorry to be a thicko, but I having a problem with the fix. I am crap at finding my way round in linux and don't understand how to apply the fix to get my video working in skype Tudor, I can't even find a skype file through terminal let alone run gedit.

Perhaps some kind patient sould could take pity on me and reply with a set of idiot proof instructions for me to follow.
Cheers

steve, (feeling very foolish)

---

### Post by tudor117 on 2010-01-26
Hi Steve,

That's fine, no problem. Let's try it the graphical way. In a terminal run:```

gksudo nautilus
```
This will make you open the file browser with super user permissions. Navigate to **/usr/bin/** and find skype. (It will take some time to load all the files.) Next rename skype to **skype.real**
Finally right click and make a new text document (Create document -> Empty File). Name this new file **skype**. Open it (double-click should work) and paste the following code inside:
```

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

```
Save the file and close the text editor. Lastly, the file must be executable. Right click it (*skype*) and go to properties. Go to permissions and click the checkbox that says "**Execute**".
That should do the trick. Close the file browser and test it out.

---

### Post by angliski on 2010-01-27
Tudor, this is the message I get

steve@steve:~$ gksudo nautilus

** (nautilus:2861): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2861): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2861): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Shutting down nautilus-gdu extension

(nautilus:2861): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
steve@steve:~$ 




Steve

---

### Post by angliski on 2010-01-27
Tudor.
absolute disaster. Followed your instructions when browser came up, found skype, renamed to skype real. Made new file and got into gedit. copied and pasted, hit execute came out. No skype at all, firefox won't load at all, computer hangs. Had to shut down and restart in windows, (yuk) to get this message to you.

Big problem HELP

Steve

---

### Post by angliski on 2010-01-27
OK so I decided after several hours of a frozen computer to do a fresh install. Downloaded iso file, burn to didk and installed 9.10 no probs.
Wireless now doesn't work, it was OK) and when I try to install skype, deb package manager gives me,"libqt-4 network needs to be installed. I've looked in synaptic and cannot find any libqt files. Where can I get them from.

Steve

---

### Post by tudor117 on 2010-01-27
WOW I'm speechless...

Well... I really don't know what to say. One of the possible things is that there may be something bad about your hardware?!? When my firefox started crashing randomly I apparently had my RAM crashing. That may be a possibility. Especially because weird things happened after a clean install.

So let's recap what you did. You rename the file named skype, and then created a new file with that code inside. Hmm.. That shouldn't have broken anything. 

Are you using Ubuntu 64bit or 32bit? And where are you getting your skype from? Mine is from the [skype website]("http://www.skype.com/download/skype/linux/choose/").

About the nautilus errors, I get some too. I don't know what they mean I just ignore them and it works fine. In case you're interested here's what I get: ```

Initializing nautilus-gdu extension

** (nautilus:4914): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4914): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4914): WARNING **: No marshaller for signature of signal 'ShareCreateError'

```
But your windows works. That's really weird. I have absolutley no idea.
The weird thing is your error about contacting an admin. I don't much about that..

As for the qt package. I believe the package is libqt4-network? I have it in synaptic. Is the multiverse repository enabled? Try going to System -> Administration -> Software Sources and enabling multiverse, universe and all.

If you try skype again, try simplifying the lines and putting just:
```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

```
And, (if you get this far) run skype from the terminal so that we can see the errors it gives.

Are you running compiz by any chance?

Anyhow... Good luck :)

---

### Post by angliski on 2010-01-28
Hi Tudor

OK, after shutting down again and restarting everything worked after a bit of a fiddle with the wireless setup. Eventually found the libqt files and installed skype, (from skype website) Still no video so I went to the wiki site and printed off the list of cams that work out of the box with linux skype, (trust procam). It should be here by Monday, so I'll try it and let you know. It has much better resolution than my pc-line 300, which according to wii only works after a fair bit of fiddling.

Thanks for the help and advice, much appreciated. I will however try to find out why I get this strange error message regarding no permissions.

Cheers

Steve

---

### Post by tudor117 on 2010-01-28
Hi Steve,

Its great that you have it working. I assumed before that your webcam worked (never thought that you haven't tested it before). A way to test it is to install cheese. Its a webcam app. If it works with cheese, chances are it should work with skype. 
The script we made here is supposed to help 64bit systems have webcam work with skype. I believe that 32bit systems should work out of the box.

I went about to read about your nautilus problem. Apparently its a windows share problem. Try to install samba.
```
sudo apt-get install samba smbfs
```
From this thread: [http://ubuntuforums.org/showthread.php?t=566572]("http://ubuntuforums.org/showthread.php?t=566572")

---

### Post by angliski on 2010-01-29
Hi Tudor
I don't think I'm running compiz. What is it, what does it do and does it start automatically.
No, the webcam never worked It's a PC-Line 300 and the wiki site says that it doestn't work without quite a bit of fiddling. I am hoping that the new cam will work as wiki says it does, "straight out of the box"

Let you know what happens.

PS: I've installed samba.

Steve

---

### Post by gradinaruvasile on 2010-01-29
Running Nautilus in root mode is a bad idea IMO.
Run only gedit or wahtever text editor you have. Nautilus is a complex beast and you may mess up your permissions to certain files that are essential to the GDM.

The Skype solution is simple, no need to fiddle around messing stuff up.
Try the command with the LD_PRELOAD in a terminal. 
Then if you want to make it permanent:

```
gksudo gedit /usr/bin/skype-launcher
```

Or, in Xubuntu is mousepad instead of gedit.

and paste the following in it:

```
#/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

save, quit. Then type:

```
sudo chmod +x /usr/bin/skype-launcher
```

And if you use 64-bit version of ubuntu the path to the v4l1compat.so is slightly different:

/usr/lib32/libv4l/v4l1compat.so


Then launch the menu editor (press alt+f2, type alacarte, enter), and modify the Skype launcher command there (from skype to skype-launcher).

Thats all. 

Also, the best working version (yes, i tried it and use it on 8 computers and it works perfectly) is directly from the Skype site:

[http://www.skype.com/intl/en/download/skype/linux/choose/]("http://www.skype.com/intl/en/download/skype/linux/choose/")

---

### Post by ArkyRobTerix on 2010-01-29
Hi all,

On my Intrepid with Logitech QuickCam (046d:08af) the 'Skype.real' fix worked fine for me. 

(I am amazed how many people can fix things on this forum - this is my first post!)
Thanks again and keep helping each other!

Arky

---

### Post by angliski on 2010-01-30
Just to add, I tried my wife's PC-LINE cam, she has a better model, than my 300N, a PCL 1.3MP and it worked without any problems at all.

I'm hoping that my Trust spotlight pro will be as good.

For anyone thinking of buying a cam, Amazon have got a 5 megapixel cam for £9.99 which they say works with Linux. No Brand name in the tech spec tho'

Cheers everyone for your help and suggestions

Steve

---

### Post by drpaul on 2010-01-31
I have recently installed 9.10 with the latest package from skype. Previously I ran 8.04. Both audio and video functioned. Now I only have audio. The video device is

Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

Cheese works.

I tried the script suggested in this thread to no avail. With or without, the little blue light on my laptop camera lights up when I click on the TEST button in the Skype options, but the little video window remains black.

Anybody have any suggestions?

TIA

Paul

---

### Post by tudor117 on 2010-01-31
Drpaul,

Make sure your camera works in ubuntu 9.10. Try cheese or a program like that. I've read that your camera may have issues? What camera is it exactly?
For exmaple, see [[COLOR="Navy"]http://ubuntuforums.org/showthread.php?p=3847488#post3847488[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3847488#post3847488")
Good luck.

---

### Post by angliski on 2010-02-02
Have you tried deleting the latest skype, 2.1.0.xx and re-installing 2.0.0.xx?

Cheers

Steve

---

### Post by angliski on 2010-02-02
New Trust spotlight pro arrived this morning. works straight out of the box on both Linux and Windows, (spit, spit, but I had to test it!) excellent picture quality.

Thanks to all of you who tried to help me with my problem. i guess it just a cheap naff camera and wouldn't work even if John Logie Baird had set up the video.

Steve

---

### Post by drpaul on 2010-02-04
thanks for all of the suggestions. as my earlier post mentioned cheese is working.

I tried to go back to 2.0.0; video worked but sound did not. I tried 2.1.0.47 and everything seems to be working.

Hope that this helps others.

Paul

---

### Post by JGMS on 2010-05-21
Whilst reading through the items I wondered why nobody takes the easy route, simply by adjusting the main menu call.

In System/Preferences/Mainmenu select Skype whithin the Internet part of "Applications". Then in "Properties" change the execution line by typing **excactly** the phrase :

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

for a 32 bit version of Ubuntu

or

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

when you have installed a amd64-version of ubuntu.

---

### Post by labinnsw on 2010-06-05
> **tudor117 said:**
> If you installed from skype's website (the new beta) there will be no skype.real but only a skype executable. You need to rename it to skype.real

Thanks, you are a God send. [The complete solution is posted here.]("http://ubuntuforums.org/showpost.php?p=9419207&postcount=50")

---

### Post by huangja123 on 2010-11-10
This works for me too, at least the Test. I have not tried a chat.

Video is not working in Google Chat too. It is a plugin. Can this script be applied? How?

---

### Post by rdaneel76 on 2010-12-12
The only solution that worked for me was to downgrade to 2.1.0.47. I was able to find the .deb here: [http://download.skype.com/linux/skype-debian_2.1.0.47-1_i386.deb](http://download.skype.com/linux/skype-debian_2.1.0.47-1_i386.deb)

I tried all of the other solutions involving lib4l1compat.so etc., but nothing worked. I have an hp pavilion dv2000 laptop with an inbuilt webcam. lsusb tells me it is the following:

Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

I had to spend the better part of a day figuring this out, so I hope it helps someone.

---

### Post by beew on 2010-12-12
Just see this thread. I am having problem with Skype video in Maverick. Sounds works, built in webcam works in Cheese out of the box but skype's video test just shows a blank box.  I have created a thread in the absolute beginner section.[ http://ubuntuforums.org/showthread.php?t=1643387]("http://ubuntuforums.org/showthread.php?t=1643387")

If anyone stumbling on this thread knows of a way to help, it would be much appreciated.

---

### Post by labinnsw on 2010-12-13
See the link in my post ([#36]("http://ubuntuforums.org/showpost.php?p=9419207&postcount=50"))

---

### Post by mrtom21 on 2011-04-08
Hi all, I found a solution that is meant for mint, but it worked for me perfectly fine on Maverick 10.10.

I'm using a Logitech Quickcam, and Skype Beta 2.2.0.25.

[http://forums.linuxmint.com/viewtopic.php?f=42&t=61103](http://forums.linuxmint.com/viewtopic.php?f=42&t=61103)

Hope this helps others. Its a fairly simple solution too!

---

### Post by alsk on 2011-04-12
Thank you for sharing! Great! :D

After the recent updates I lost Skype (2.2.0.25 32-bit) video too, and the Mint fix works... which is to force v4l compatibility library to be loaded along running skype.

To save you from looking, for my system this makes video work: 
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

The system is:
- Ubuntu 10.10 32-bit, just stock stuff
(a bit shameful, but it's running on Athlon64, as I gave up with 64-bit after years of struggle)
- Kernel 2.6.35-28-generic  
- Labtec Webcam Pro, lsusb: Bus 003 Device 002: ID 046d:08a2 Logitech, Inc. Labtec Webcam Pro
- NVIDIA FX5900XT, nvidia closed driver
- Skype (beta) 2.2.0.25






.

---

### Post by gael666666 on 2011-04-25
hey,
i'm a beginner in ubuntu and i don't know so many thing about computers, but the video of my skype (2.2.0.25 32-bit) is not working. when i type the given command in my terminal (LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype), video is working. but it's not very convenient to type this command every time i want to open skype. is there any easier way to fix skype always working with video??
thanks in advance.
gael

---

### Post by tudor117 on 2011-04-25
Hi gael,
You can make a script to do this for you. There's multiple ways, but here's my way of doing it.
First move the real skype:
```

sudo mv /usr/bin/skype /usr/bin/skype.real 
```
Next, create a launcher for your skype (this will open in gedit, you can alternatively use nano, or etc.)
```

gksudo gedit /usr/bin/skype 
```
And paste in the following: [**32 bit** users only]
```

#! /bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype.real

```
Save and you're all done. Launch skype, and you're good to go. You can try it from the terminal first, not that it matters...

Alternatively, for 64bit users, paste the following: [**64 bit** users only]
```


#! /bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype.real "$@"

```

---

### Post by Tanjerine on 2011-04-26
Strange. What finally worked for me (just now) was not the LD_PRELOAD, but I had downloaded and installed v4l2ucp and I ran it while testing skype's video. It turns out I had to disable the Power Line Frequency to finally get it to work (lighten up).

---

### Post by herbest on 2011-04-28
I have kubuntu 10.04 LTS.
I have skype 2.2.0.25.

When I video call, I get a black video screen. I see my preview. The person I am calling sees me. Bu I can not see her.

I have tried the following solution:

1) edit a skype.real file
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0

2) run it from a terminal

It did not improve.
When I close the call, I get the following message:

"libv4l2: error dequeuing buf: Argument invalide"

I am stuck. I spent all day looking for a solution.

Thanks for any help

---

### Post by totololoto on 2011-06-07
Hi there,

I have exactly the same configuration (ubuntu and skype versions)  and the same problem as Herbest described.

Is this the right thread to get tips about that ?

If anyone can help, thanks a lot,

---

### Post by tudor117 on 2011-06-07
Are you (totololoto and herbest) running 32-bit versions?

Also, make sure that in the skype options under "Video Devices" you have selected an appropriate selection for "Automatically receive video from..." option. As a test, try "anybody".

By the way, is the error *"libv4l2: error dequeuing buf: Argument invalide"* in English? Either way, that shouldn't have anything to do with what YOU can see, it is about your camera.

Last thing, are you using compositing (i.e. compiz)? I don't think it has an effect any longer but try disabling it for a test call.

---

### Post by totololoto on 2011-06-13
Hi,

I am running the 32bit version of skype (and my ubuntu is 32 bits as well).

I am launching :
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

The messages I'm getting in the console are :
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
libv4l2: error dequeuing buf: Invalid argument
libv4l2: error dequeuing buf: Invalid argument
libv4l2: error dequeuing buf: Invalid argument
libv4l2: error dequeuing buf: Invalid argument

(so in english...)

I have checked 'anybody' for "automatically receive video from..."

And at last compiz is not installed on my system (I removed it previously).

But I cannot get see the video from my correspondant.

Thanks for your help,

---

### Post by tudor117 on 2011-06-13
I believe that the new skype uses v4l2 instead of v4l1 (which you used).
Try running skype with:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
also make sure the package *libv4l-0* is installed.

Just fyi, I find it weird that YOU can't see... 
Are you running Cairo dock? Or any other software that didn't come out of the box? I'll try to replicate this if the previous command doesn't fix it.

---

### Post by Sleepy-zz-John on 2011-06-15
Hi folks!    Let me add my own recent experiences and issues to this wonderfully informative thread :) 

I'm using a cheap USB webcam which identifies itself with lsusb as:

```
BUS 005 Device 002: ID 18ec:3290 Arkmicro Technologies Inc
```

Until a couple of days ago I was using this reasonably happily on Karmic 9.10 with Skype 2.2.0.25 which I opened with terminal command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
```

Apart from the odd times when I forgot to plug the correct USB lead in,  this generally worked fairly reliably.

Yesterday,  I upgraded from Karmic 9.10 to Natty 11.04.   (very nice but it's a new learning curve to find where everything is there! :confused:)

OK,  so first of all I tried opening Skype in Natty with my same old LD_PRELOAD....vl4l1compat.so  code.   Result: Skype came up OK but no webcam pic at all,  only a blank test screen.

Next I installed Cheese and tried the camera there,  and that worked fine.

So then I retried restarting my laptop and starting Skype with the same old LD_PRELOAD again.  This time it all worked.   Pic was good.  

But next time I tried to test the webcam in Skype,  it completely crashed and froze my whole Natty. 

More tests resulted in about 50% successes and 50% complete Natty freeze-crashes.   

At this point I read this thread,  moved my /usr/bin/skype to /usr/bin/skype.real and created a new "skype" file using v4l2convert.so thus:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype.real
```

This opens Skype much more nicely than entering LD_PRELOAD... from a terminal every time,  but changing to v4l2convert from v4l1compat doesn't seem to have had much effect on the incidence of freeze-crashes when I test my webcam in Skype. 

This makes it look as if Natty is much more sensitive than Karmic and crashes very easily when it sees my cheap webcam.   Karmic was much more robust.    Is this a credible theory do you think?   How could I put it to the test?   

I notice that the Skype site now has a new version on offer: 
"skype-debian_2.2.0.35-1_i386.deb",  so maybe this might be an answer?   Otherwise maybe it's a new webcam I really need? 

Any thoughts or experiences, anyone?

---

### Post by totololoto on 2011-06-15
I am sorry, it still doesn't work with your tips.

Actually I cannot see the video of my correspondant. I correctly see mine (despite the libv4l error).

I am wondering why some of my contacts, on the contact screen, have a small blue picture showing a camera with a tooltip saying 'this contact is configured for video conferencing' and others don't.
The contact whose video is not visible for me has not this blue picture but I used to be able to see his video with the version of ubuntu and skype I used before.

I have not tested video with contact who have the blue picture. Could that be a reason why it doesn't work ? How to get skype understand that my contact can be configured for video (ie has a webcam which works).

Another information : when I am connected with the contact from which I cannot see his video, I can see very quickly, from time to time, something that flashes on my full screen. Like if my screen becomes black for a very short fraction of a second...

I have looked at my syslog file, but I cannot see any messages which may be obviously related with this video problem.

thanks again for your help.

---

### Post by tudor117 on 2011-06-15
Sleepy-zz-John, it might be that skype and Natty don't get along or that either of them is unpolished. I am not quite sure how you can test it other than having same software (to a certain extent) and same hardware running the same thing...

Totololoto, I am completely stumped. Have you tried the video with other contacts? Can you see yourself if *only you* are sending video? If not, can you see yourself in the skype video test (in the options)? Also, what graphics card and driver do you have? The fact that it flashes randomly should indicate that SOMETHING is working...

---

### Post by Sleepy-zz-John on 2011-06-17
> **tudor117 said:**
> Sleepy-zz-John, it might be that skype and Natty don't get along or that either of them is unpolished. I am not quite sure how you can test it other than having same software (to a certain extent) and same hardware running the same thing...
Thanks. Yes,  I'm also coming to the conclusion that Natty isn't as compatible with Skype as my Karmic was.  I've now upgraded my Skype from 2.2.0.25 to 2.2.0.35-1 without any improvement.  50% of the time I'm still experiencing Natty crashes when I test my webcam in Skype's Options - Video Devices.  The crashes are now consistently taking the form of fullscreen fast-running white text on a black background which nothing will interrupt apart from a forced power down.     These crashes only seem to happen the 2nd time I try to test my webcam in Options - Video Devices,   not the 1st.   I'm thinking about submitting a bug report,  but not sure if I can be specific enough for the exact cause to be identified yet.

---

### Post by j.h.klein on 2013-01-16
> **oscarmeyer51 said:**
> Additional solution (not related to cairo or QT?).

For 32-bit Karmic Koala, I found this thread & solution. I have included the preload for the /usr/lib and the /usr/lib32. For me the former works and I assume the latter works for 64 bit (as skype runs in 32 bit).

Thread:  [http://forum.skype.com/index.php?showtopic=411441](http://forum.skype.com/index.php?showtopic=411441)

ig-88 posted the lib32 solution (Part 1) and Part 2 was posted by the_wOndErEr57 and gradinaruvasile (yes, I had to see my solution twice before I realized that lib32 and lib were not the same...<grin>).

Solution:

Part 1 posted was:

i use a "046d:08d9 Logitech, Inc. QuickCam IM/Connect" on ubuntu 9.04 amd64. the webcam just shows garbage while testing and simply shows nothing in calls.

a workaround is to move /usr/bin/skype to /usr/bin/skype.real
install lib32v4l-0 via apt-get and create a new /usr/bin/skype with the following content:
CODE
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real
#################

Part 2 Posted was:

QUOTE (gradinaruvasile @ Fri Aug 28 2009, 17:15)
Go to the original post
I have a
0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam

on Ubuntu 9.04 and it is working only with the ld_preload thingie mentioned before.
BUT the path is incorrect (maybe a distro thing?) the correct command is this one:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

****************

In summary, 
1. sudo mv the /usr/bin/skype binary to /usr/bin/skype.real
2. sudo gedit /usr/bin/skype
   (or your favorite text editor instead of gedit)
3. copy & past into the editor the following

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

4. enter "sudo chmod 755 /usr/bin/skype" without quotes to make the script file executable
5. start skype via the menu and test the video
#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype.real

for Ubuntu 12.10 64 bits

Thanks so much!

---

### Post by overdrank on 2013-01-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

