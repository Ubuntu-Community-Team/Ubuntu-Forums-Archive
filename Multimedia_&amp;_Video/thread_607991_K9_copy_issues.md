---
title: "K9 copy issues"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by mastergunner on 2007-11-09
Guys I have been having problems with ripping DVD's. K9 copy use to rip and then copy a DVD. Mine rips and copies the DVD BUT the Main Screen menu doesnt work and you have to actually hit the play button on a DVD player to make it play. Somehow when it copies it loses the links from the main menu. What is going on here?

---

### Post by Anlace on 2007-11-09
Greetings,

I experienced that before though it's been a while now since I've had it happen.  I remember something about having to get the correct libraries to copy/play DVD Menus.  Does it play alright in a regular DVD player?

Anyway, it's not much help but maybe that will help in your search.

Peace,
Gail

---

### Post by mastergunner on 2007-11-09
It plays but goes straight to the movie when I put it in a DVD player. CAN ANYONE ELSE HELP????

---

### Post by franny on 2007-11-10
In my experience, I had to find the2 sets of library files - the libdvdcss files can be found in synaptic package manager. 
After that dvd backup worked great. 

No actual program seems to be used for the initial full size copy and it works right off the desktop.

When I put a dvd in, of course, movie player starts. 
I shut the player down and locate the dvd drive icon that appears on my desktop with the dvd title
I RIGHT CLICK the icon and select 'copy dvd'  
Now a little window opens where I select the format option for an iso (a disk image) and I save to a folder on my desktop.

Then I compressed the file with K9copy, save as the same name and same location (eliminating the full size version), and after compression I can burn a disc with k3b. 
No problems except for 2 recent dvds I ran into that seem to resist all attempts.
We are still working on solving this issue.

Meanwhile,  what's the skinny on dvd "back-up" with the new 7.10 release?

---

### Post by mastergunner on 2007-11-14
Well K9 is still not working like it did in &.04. It just does not want to copy the DVD with working menus even when I tell it to. Can anyone help????????????/

---

### Post by Rhubarb on 2007-11-14
Make sure you've got the main DVD (and all the Titlesets) checked.
k9copy works fine for me here.

---

### Post by franny on 2007-11-14
> **mastergunner said:**
> Well K9 is still not working like it did in &.04. It just does not want to copy the DVD with working menus even when I tell it to. Can anyone help????????????/

Hmmm... did you get both of those library files? libdvdcss*

You might try to contact the K9copy developer and/or just re-load the latest version.

My son got in touch with the guy regarding it's problems and apparently (the developer) has worked on a fix. - and ??may?? be working on it further still.
And now it works well for me.
However, I did run into 2 movies recently on DVD that while I could create my "back up" copy from my desktop with a right click - K9copy was not able to compress them. These may have a different blocking process because everthing else I back up seems to respond normally.

Wish I knew more and could help you out, but this is the limit of my experience.

Good Luck

---

### Post by mastergunner on 2007-11-15
Yes I check all of the titlesets. It is just that the Main Menu of the movie doesnt even come up or if I do get it to come up the links are not working. I have also uninstalled K9 and then reinstalled and still have the same problem. I have the libdvdcss2 file as well as the codecs. Anyone else with any answers?

---

### Post by Shampyon on 2007-11-16
I know you said you made sure all of the titles in the DVD are selected, but is the option "Keep Original Menus" (bottom right in Rhubarb's attached image) checked? I've found that one or two DVDs will have odd titleset numbering that will cause some errors if you don't. I only uncheck that box when I'm only ripping the Main Movie.

---

### Post by Aquaman420 on 2007-11-16
If the dvd is made by Sony it might not not have css.  It might have  arcoss, which I don't think k9copy has support for yet.

---

### Post by franny on 2007-11-25
> **mastergunner said:**
> Yes I check all of the titlesets. It is just that the Main Menu of the movie doesnt even come up or if I do get it to come up the links are not working. I have also uninstalled K9 and then reinstalled and still have the same problem. I have the libdvdcss2 file as well as the codecs. Anyone else with any answers?

> **mastergunner said:**
> Well K9 is still not working like it did in &.04. It just does not want to copy the DVD with working menus even when I tell it to. Can anyone help????????????/

I think the author may still be working on ta major bug- but he may need to hear about others - like the Sony disc issue, as per **Aquaman420**.

Why don't you or someone else who feels up to the conversation contact him and see where he's at, and mention all the other issues you know about. 
**In the K9Copy help menu click on report bug**.

I have run across a few newer discs where I've had trouble copying, though most work out OK

---

### Post by mastergunner on 2007-11-25
I have tried to contact him and have received no answer and it has been 2 weeks.

---

### Post by mc4man on 2007-11-25
K9copy should handle any dvd title without structure protection.(or an unusual non protected structure) As far as s.p. titles there are some it can't deal with and others that it can with some possible limitations. Overall it (or any linux only solution) won't be able to keep up with protections that are being actively updated. There is a newer ver. (1.2.0) but you'd need to compile it yourself, I wouldn't expect a ubuntu update till Heron.
There are 3 major types of s.p. - sony ARccOS, ripguard, and what could be called protectdvd 
ARccOS  is fairly rare, a handful of titles per year, the last R1 were last spring, worldwide since then only spiderman3 R2 that I'm aware of. ARccOS doesn't change from one ver. till the next ver. so any solution is good for quite a while. K9 doesn't do well with ARccOs, there is an almost linux only solution but not worth the effort. 
The protectdvd type of s.p. again is fairly rare - some german releases and more recently from new line cinema. The first N.l. ver. had a linux/wine solution, the latest is only practical using defabhd.... in wine or windows. The latest N.L. titles won't even play in linux except with Lindvd player
The most common s.p. is ripguard which comes in several variations and is updated/modified very often. K9 can do alot of ripguard titles though you need to make some adjustments. Sometimes movie only w/ orig. menus, or movie only no menus(reauthored), occasionally you can do the whole disk. You need to look through the titlesets and remove any bogus titlesets/titles from the rip. Sometimes there will be bogus titles in the titleset with the main movie, more often there will be bogus titlesets/titles spread out over the disk with some butchered menus to boot. Size is usually a good indication something is amiss.

---

### Post by mastergunner on 2007-11-26
So how do compile the new version? Also how are you adjusting your movies and finding the bogus parts?

---

### Post by mc4man on 2007-11-27
Here are the depends if you want to compile k9.
```
sudo aptitude install libdvdread3-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev

```
If your inclined to try it use checkinstall - makes it easier to remove
I've got to get to work - if you have a particular title in mind post it, I'll give you a solution - once you do/see one it becomes much clearer

edit: just compiled 1.21 works pretty good though needed some add. packages for the make,  i did several at once, probably libavcodec-dev and libaformat-dev did the trick.

---

### Post by mastergunner on 2007-11-27
I just copied and pasted that into terminal. It went through the process but now what? Did that do the upgrade? I just looked at the verion in K9 and it states 1.1.3 so did I do something wrong?

---

### Post by mc4man on 2007-11-27
if you want to go ahead and give this a shot what you dl'ed was just the depends.
You would need to uninstall your present version. Go to the k9 web site and dl the latest ver. Inside is a text file called install which you should read thru. It's pretty straightforward. (Do a search on compiling K9copy if you're unsure)
There's no saying this ver. will be any more effective than the current gutsy ver. You still may need to make some choices depending on the title.
Personally I find these s.p.'s interesting to understand and overcome but if you're looking for a complete solution with little or no user input/analysis then in the long run install wine and a couple of free progs.

---

### Post by mastergunner on 2007-11-27
I have wine and use dvd fabdecrypter but I havent found anything that will compress and copy it onto a standard DVD. DVD Shrink apparently doesnt work. You have anything else that will work? What is the K9 website?

---

### Post by Shampyon on 2007-11-27
[http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)

Choose "Downloads" from the menu at the right, and download from the relevant link under "Sources"

As mc4man said, the instructions are in a text file called "INSTALL" inside the tar.gz archive.  They're relatively easy to follow. If you've never installed from source before, make sure you read the instructions carefully

---

### Post by mc4man on 2007-11-28
I believe there are some issues with defabhd and dvdshrink, try latest update 
[http://club.cdfreaks.com/f116/dvdfab-platinum-ripped-files-incompatible-other-programs-232255/](http://club.cdfreaks.com/f116/dvdfab-platinum-ripped-files-incompatible-other-programs-232255/)
Did you try running the defab rip back thru k9 for transcoding?
A very useful app for some titles is vobcopy 1.02 , before compiling edit the # of tries from 9 to 1 
 ```
while( ( blocks = DVDReadBlocks( dvd_file, i, file_block_count, bufferin ) ) <= 0 && tries < 10 )
                        {
                          if( tries == 9 )
                            {
```

---

### Post by mastergunner on 2007-11-29
How can you have K9 just transcode and not rip? Where do you get vobcopy?

---

### Post by wjston on 2007-12-22
> 
edit: just compiled 1.21 works pretty good though needed some add. packages for the make,  i did several at once, probably libavcodec-dev and libaformat-dev did the trick.

Thanks for your advice. Helped me resolve my issues with dvd's not playing in standalone dvd player. Just wanted to note that libaformat-dev is missing a "v." Should be libavformat-dev. I used your post to build the latest K9copy version 1.2.1 and I am watching my first successful backup since the release of Gutsy.  Thank you for your help. I have tried many different scenarios but all failed until now. Just like to say [COLOR="Red"]"Merry Christmas"[/COLOR] [COLOR="SeaGreen"]to you and everyone else monitoring this forum. This was a Christmas gift for me.[/COLOR]

---

### Post by mastergunner on 2007-12-22
So exactly what are the steps on how to install the update k9?

---

### Post by mc4man on 2007-12-22
Well I can't type for sh.. so I'll just give you the short of it, between earlier in this thread and in [http://ubuntuforums.org/showthread.php?t=645804](http://ubuntuforums.org/showthread.php?t=645804)   i'm sure you can put it together
Compile, install, run k9.. are 3 _separate_ things
dl source
install build depends (packages)  note if any installed packages are removed
remove current k9
configure (source)
make
install
run (use)k9..

---

### Post by mastergunner on 2007-12-22
mc4man thanks for the help but I am a noob at linux so if you could please give me the full instructions, THnaks.

---

### Post by wjston on 2007-12-22
> **mastergunner said:**
> mc4man thanks for the help but I am a noob at linux so if you could please give me the full instructions, THnaks.

First, uninstall the version you have installed using Synaptic Package Manager (System>Administration>Synaptic Package Manager then Search>type k9copy).

Next, make sure you have all the dependencies prior to the build. This can be completed by using Package Manager (use the search engine and find the dependencies your system doesn't have), or you can use a Terminal - Applications>Accessories>Terminal - then use the following command:
```
sudo aptitude install libdvdread3-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev libavcodec-dev libavformat-dev
```

Download the most recent version of k9copy from here: [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)
Extract the file to your Desktop (right click on the file and choose "Extract Here").

In a Terminal (type)```
 $: cd /home/your_username/Desktop/k9copy-1.2.1
                                 $ ./configure
                                 $ make
                                 $ sudo checkinstall -D make install
```
Answer all questions with the default answer by hitting Enter.

Next, create a link to K9copy with: ```
sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy
```

and then create a menu entry - run
```
gksudo gedit /usr/share/applications/k9copy.desktop
```

and paste this in and save
```
[Desktop Entry]
Name=k9copy
Comment=DVD ripper
Exec=k9copy
Icon=/usr/local/kde/share/icons/hicolor/48x48/apps/k9copy.png
Type=Application
Categories=Application;AudioVideo;
```

Note: credit/thanks for above to kpkeerthi and mc4man

---

### Post by mc4man on 2007-12-23
this is basically for doing on a fresh install of gutsy though i noticed some things when installing a compiled 1.2.2 after removing 1.2.1 (compiled)
for fresh or if you have repo ver.of k9 remove it and only use applicable parts
install all the updates and if planning on using advanced desktop effects install compizconfig-settings-manager (generally get your desktop, video squared away)
after that go to software sources and for the moment enable backports in the update section
run in terminal
```
sudo aptitude install libdvdread-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev libavcodec-dev libavformat-dev
```
after that go to this site -  [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)  and dl the libdvdcss2 deb to your desktop and install (or do the medibuntu thing)
you can grab the libdvdcss2-dev also, won't hurt
Now you can either install these packages or install k9 from repo and then uninstall (I think it's better to install the apps). The point is satisfy what k9 needs to run or may use for certain features
mplayer, mencoder, ffmpeg,  dvdauthor, vamps, x264  (x264 is only needed if you are going to use it, can leave off)
```
sudo apt-get install mplayer mencoder ffmpeg dvdauthor vamps x264
```
double ck. in synaptic that libdvdnav4 is installed.
If wanted run updates from update manager - not needed for this (latest compiz-fusion ect.) then disable backports (safer in long run)
Dl from k9 site k9copy-1.2.2.tar.gz to desktop and extract there - then run in terminal
```
cd Desktop; cd k9copy-1.2.2
```
followed by ```
./configure --prefix=/usr
```
when thats done run 
```
sudo checkinstall
```  follow the prompts and that should do it
If successful k9 should have been installed to /usr/bin/ - may want to ck.
To create menu - right click applications > edit menus, highlight sound and video and click New Item. In the create launcher box add name, for command ```
 /usr/bin/k9copy
```  double click the icon box and paste in 
```
/usr/share/app-install/icons/k9copy.png
``` in the address 
or leave off k9copy.png if you want to choose an icon
As far as going from 1.2.1 compiled to 1.2.2 I'll edit back in
edit:
the 2 minor issues when doing the make/install of 1.2.2 after removing 1.2.1 (maybe from not doing complete removal - don't know) were first the link in /usr/bin wasn't deleted causing an error referring to such and 2nd, at the very end of the install an error about failure to overwrite some doc file. Don't remember which one but if it comes up the solution was to install/uninstall the repo ver. - that squared up the problem whatever it was

---

### Post by mastergunner on 2007-12-25
Hey guys I followed the above and it installed successfully BUT when I went to rip and burn I had a problem. After the DVD ripped it crashed not once but twice. So what did I do wrong? I went ahead and removed it then installed k9 from Adept. I had no problem with it then. SO what is the deal?

---

### Post by mc4man on 2007-12-26
In all likelihood you did nothing wrong. There's nothing to say ver.1.2.1 is any better than 1.3.1 or that  a self compiled package is as good as the one in the repo, or k9 wil work on every title in all backup configs. I only tend to use k9 as a ripper and /or processor in certain situations so the latest version makes sense. As far as processing I usually use an encoder and for iso building and burning I still use ImgBurn cause it's 100% successful and has a lot of options and info. But for the purpose of testing 1.2.1 I let k9 rip, process, and create iso with 5 titles - 2 full disk, 3 movie only. I used the built-in cd/dvd creator to burn some dvd-rw's , they all came out fine, played fine. The quality was actually good to very good.
As far as your problem it would be impossible to tell without very specific  info, plus it wouldn't hurt to run out of the terminal for any possible error messages

---

### Post by glaze0101 on 2007-12-26
I am having the same problem.  I made one backup no problem, but this one keeps crashing. oh well.

---

### Post by mastergunner on 2007-12-26
So can you tell me exactly what I should do? Reinstall and try again or what?

---

### Post by mc4man on 2007-12-26
@ mastergunner  Post the name of problem title if not here edit it into your post at cdfreaks

---

### Post by mastergunner on 2007-12-26
What post at cdfreaks?

---

### Post by Cubby on 2008-01-24
> **wjston said:**
> First, uninstall the version you have installed using Synaptic Package Manager (System>Administration>Synaptic Package Manager then Search>type k9copy).

Next, make sure you have all the dependencies prior to the build. 
 
Hi again, wjston,

I just wanted to thank you for redirecting me to this post from another post I wrote where I was having installation problems with k9copy.

In that time I switched from ubuntu  Feisty Fawn, to Kubuntu 7.10.  I'm more familiar with the KDE desktop, which is the main reason I made the switch.

Anyway, I had many dependencies that I needed to install, and I could give you a long list of my notes of the three days of work involved, but I will spare you that.:)

I just installed the latest version put up by source forge, version 1.2.3 and hey, it's even in my system menu.  

I will give this version a try and let you know how it works if I have anything to add.

Again, thanks to all for the help, 

Lisa Marie

---

### Post by wjston on 2008-01-27
> **Cubby said:**
> Hi again, wjston,

I just wanted to thank you for redirecting me to this post from another post I wrote where I was having installation problems with k9copy.

In that time I switched from ubuntu  Feisty Fawn, to Kubuntu 7.10.  I'm more familiar with the KDE desktop, which is the main reason I made the switch.

Anyway, I had many dependencies that I needed to install, and I could give you a long list of my notes of the three days of work involved, but I will spare you that.:)

I just installed the latest version put up by source forge, version 1.2.3 and hey, it's even in my system menu.  

I will give this version a try and let you know how it works if I have anything to add.

Again, thanks to all for the help, 

Lisa Marie

Your very welcome. It is a pleasure to be able to give back to this forum as I have been on the "need help" end many times in my quest to ditch Windows. I have another link that will help alleviate all those dependency problems for you.The members who developed the fix did a fantastic job and I salute them for their genius and I thank Cappy for posting the howto. 
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

