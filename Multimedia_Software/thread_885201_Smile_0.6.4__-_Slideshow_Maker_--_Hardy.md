---
title: "Smile 0.6.4  - Slideshow Maker -- Hardy"
date: 2008-08-09
forum: Multimedia Software
---

### Post by lubeck on 2008-08-09
The new 'SMILE' SLIDESHOW. An install process that worked for me on 8.04.1
(Translated from a French UBUNTU Forum) ... WAS EASY FOR ME, A NEWBIE.

**SMILE 0.6.x INSTALL ON HARDY 8.04.1  - worked as of 8/9/08 (Used 0.6.4. Should work on later versions.)**

**Install the dependencies** (libogg-dev,livorbis-dev,libmad0-dev and others in line below, if not present) using Synaptic or use the following in Terminal.  Synaptic worked well for me for validating what is there and downloading--if you are not familiar with Terminal:

sudo apt-get install libogg-dev libvorbis-dev libmad0-dev build-essential fakeroot checkinstall mplayer mencoder imagemagick

**Uninstall existing SOX using Synaptic, if installed (you can check,as always, using Synaptic)**, or use this command at the terminal:

sudo apt-get remove - purge sox 

**Download latest version of SOX** in its compressed form, then UNPACK the download in a folder you create, like &#8220;sox-14.0.1&#8221;...  SOX compressed file may be found at: [http://sourceforge.net/project/downloading.php?groupname=sox&filename=sox-14.0.1.tar.gz&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=sox&filename=sox-14.0.1.tar.gz&use_mirror=internap)
Go to the location where you unpacked all the SOX files,for example: 

cd /home/g/sox-14.0.1 

(**NOTE:** As I have learned and I am sure you all know, a"xxx.tar.gz" folder in Ubuntu/Linux is the same as a "xxx.zip" in Windows. A ZIP folder. My approach to unzip any "xxx.tar.gz" is to simply double-click on the "xxx.tar.gz" in question, which allows you to see its contents, then to drag the folder in it to my "/home" directory.)

**Compile SOX in /usr with this command**...SMILE expects to see it in /usr and that's where this code puts it&#8212;execute one command at a time:

./configure --prefix=/usr 
make 
sudo make install
 
**INSTALL needed libraries for qt4** noted below: In Hardy, FIRST go to System, Administration, Software Sources, Updates, and select Hardy-Backports to allow loading of some of these items.  I then used Synaptic to install and it worked well.  (There are 3 libs, as you'll note, and they load others automatically.)

sudo apt-get install libqt4-opengl-dev libqt4-dev libqt4-webkit

NOTE: Per French site, if the 3 previous packages are not enough, install the packages in qt4-designer; should install dependencies missing.  The above Synaptic action worked fine for me, with no issues, so I had no need to do this.

**INSTALLING SMILE** - located at [http://smile.tuxfamily.org/](http://smile.tuxfamily.org/)  I selected 0.6.4 for American Friends.  NOW 0.6.6. 
[FYI:  "DOWNLOAD" in French is "Téléchargement" If you wish,read the 'Smile' site in English by using Google-Translate.]

Unzip the file from the site into the directory/folder where you want to put it, for example &#8220;smile&#8221;.

Go to the directory where you just decompressed it; example: 

cd /home/g/smile


 
**Compile SMILE with qt4** using these two commands:
/usr/bin/qmake-qt4 smile.pro 
make

**LAUNCH SMILE:**
At Terminal Command line, type path to executible, like /home/g/smile/smile OR Create a "Launcher" to this/your location. The Icon is located at /smile/Interface/Theme/smile.png

Note: 2 cookies are created in your home directory:. Smile.cnf is a configuration file and. Logsmile.txt which is the log file useful to trace bugs

Warning:
in cases of resettlement or installation of a new version you must delete the file. smile.cnf  using:  rm ~/.smile.cnf    
Be Advised:  Apparently, project files are not transportable between versions.

good luck...
I have not yet seen a Slideshow App this good.  Ken Burn effects are a snap.  Outstanding GUI.

---

### Post by luiska on 2008-08-10
Thanks Lubeck

Found your post and got Smile installed without any hassles. Rendered my first test and had a lovely mpg to play in Totem.


Cheers
Louis

---

### Post by 4ebees on 2008-08-12
Hi there,

Very interesting experience (haven't finished installing just yet :))

Following your instructions Synaptic tells me that to install: 

libqt4-opengl-dev libqt4-dev libqt4-webkit

I will need to allow it to remove:

apport-qt will be removed
edubuntu-desktop-kde will be removed
jockey-kde will be removed
kcheckers will be removed
kdebluetooth will be removed
kubuntu-desktop will be removed
language-selector-qt will be removed
libqt4-gui will be removed
mixxx will be removed
mscore will be removed
pencil will be removed
python-qt4 will be removed
qjackctl will be removed
skype will be removed
software-properties-kde will be removed
speedcrunch will be removed
stellarium will be removed
stopmotion will be removed
system-config-printer-kde will be removed
ubuntustudio-audio will be removed
ubuntustudio-video will be removed

So I followed your other suggestion of installing qt4-designer using Synaptic. This didn't give the same error. I then installed the 'missing bits' (eg. open-gl-dev) using Synaptic *after* designer had installed. This process did not give me the 'remove' notices listed above.

I'll let you know how I go.

The software from this guy is very well put together will professional interfaces...don't know how he manages it.

---

### Post by 4ebees on 2008-08-14
Hi there,

When I try to remove Sox to then install the Ogg supported upgrade I get the message that I need to remove:

dvd-slideshow
mandvd
mp3cd
qdvdauthor
terminatorx
ubuntustudio-audio

Is there any way around this without uninstalling and reinstalling these applications?

Thanks for any assistance provided.

---

### Post by 4ebees on 2008-08-15
The easiest things to do was merely to uninstall what I had to then reinstall it (I guess sometimes the beauty of Linux is merely having to type:

sudo apt-get install dvd-slideshow mp3cd qdvdauthor terminatorx ubuntustudio-audio

in a terminal and it's all back again :)

So now I'm going to have fun with another of this man's applications.

You've got to give it to him - he's got a great eye for GUIs. I'm going to donate what I can.

---

### Post by 4ebees on 2008-08-15
Hi Lubeck.

Can you let me know how you got a Ken Burns effect going? I can't see anything that allows this option.

---

### Post by Schroeder on 2008-08-24
Thanks alot for the HowTo.

Just FYI, I just installed **SMILE v0.7.2** with your instructions. Worked like a charm without any problems. 

I can start the program, create a new slideshow, add pictures etc. but when I click play the picture just becomes a fuzyy mess of black and white. Anybody else having these problems? 

Chris

---

### Post by lubeck on 2008-08-26
Hello.
I am glad you all are finding the instructions for SMILE install helpful.  The Forums are great that way....

Schroeder:  Sorry.  I cannot help you.  Perhaps someone else can.

BTW - I forgot to mention in the instructions that you can *UPGRADE* SMILE almost effortlessly after your first install.  Simply repeat the step: "INSTALLING SMILE."  I have found there is no need to uninstall, at least in my case.  This allows me to keep current...with the prolific author of SMILE.

I am sorry I do not visit the forums as often as I'd like.  Appreciate the help.

4ebees:  Your observations are helpful to all...  I also learned a lot about Ubuntu and Linux by doing this.  Not scary...sensible.

Ken Burns Effects are simply done by using the "X, Y, Z ..." panel in the upper left of the screen.  Also the "Effects" tab at the upper right.  It is not automatic...though once you do an effect you can apply it to all, I recall. I suggest you read a bit about... The key is learning how to use the "Flags."

---

### Post by Creative2 on 2008-08-26
really... i have not to compile nothing just do this...

[http://ubuntuforums.org/showthread.php?t=898281](http://ubuntuforums.org/showthread.php?t=898281)

---

### Post by lubeck on 2008-08-26
Thanks Creative2.  GREAT alternative.
Maybe SMILE can now go mainstream in the Ubuntu community. 
Always appreciate a Master's help!
Best to you.

---

### Post by Zetheroo on 2008-10-12
This is not working for me as I cannot install libqt4-opengl-dev.

:(

---

### Post by annietc on 2008-12-13
> **Schroeder said:**
> Thanks alot for the HowTo.

Just FYI, I just installed **SMILE v0.7.2** with your instructions. Worked like a charm without any problems. 

I can start the program, create a new slideshow, add pictures etc. but when I click play the picture just becomes a fuzyy mess of black and white. Anybody else having these problems? 

Chris

The same for me. I could start the program but it's very slow. I seem to have the same problems, it just won't play but slow and flashy then I have to force quit. I checked that I have all the above mentioned stuff installed.

---

### Post by 4ebees on 2008-12-14
> **Zetheroo said:**
> This is not working for me as I cannot install libqt4-opengl-dev.

:(

Hi there, just saw your post. If you're still having the same problem, can you let me know how you attempted to install the -dev files? Was it through Synaptic or the command line?

---

### Post by 4ebees on 2008-12-14
> **lubeck said:**
> 

4ebees:  Your observations are helpful to all...  I also learned a lot about Ubuntu and Linux by doing this.  Not scary...sensible.

Ken Burns Effects are simply done by using the "X, Y, Z ..." panel in the upper left of the screen.  Also the "Effects" tab at the upper right.  It is not automatic...though once you do an effect you can apply it to all, I recall. I suggest you read a bit about... The key is learning how to use the "Flags."

Hi again :)

Thanks for the comments.

Yes, I have had to play around with the application to get a better idea of how to use it. It's not as 'intuitive' as I'd like, but I can always write to the developer! Now, where was the e-mail address for that guy at Apple/Microsoft who I wanted to make some changes to another program LOL

---

### Post by 4ebees on 2008-12-14
> **annietc said:**
> The same for me. I could start the program but it's very slow. I seem to have the same problems, it just won't play but slow and flashy then I have to force quit. I checked that I have all the above mentioned stuff installed.

Hi annietc,

I have this installed on a HP laptop (1.6Ghz, 2G RAM, standard Intel video card) and it runs okay - not great. I also have a new desktop I built ("On the first day of Christmas...") quad-core (4 x 2.4Ghz) with 3G RAM and a 256Mb Nvidia card ("...and a partridge in a pear tree") and it runs VERY well, except the moving flag effect gives me black lines running horizontally down the image.

In summary, I think the application requires a fair bit of power to run well. I'd suggest making sure nothing else runs at all when using it. I tend to create a small number of images/effects at a time (two to three) then export the video for further processing in Kino etc.

Hope this helps.

---

### Post by annietc on 2008-12-15
> **4ebees said:**
> Hi annietc,

I have this installed on a HP laptop (1.6Ghz, 2G RAM, standard Intel video card) and it runs okay - not great. I also have a new desktop I built ("On the first day of Christmas...") quad-core (4 x 2.4Ghz) with 3G RAM and a 256Mb Nvidia card ("...and a partridge in a pear tree") and it runs VERY well, except the moving flag effect gives me black lines running horizontally down the image.

In summary, I think the application requires a fair bit of power to run well. I'd suggest making sure nothing else runs at all when using it. I tend to create a small number of images/effects at a time (two to three) then export the video for further processing in Kino etc.

Hope this helps.


Hey there, thanks a lot for getting back. 

Hmm it seems that your hardware are at good level. Mine is not that high so I am thinking perhaps it's too much for them to handle SMILE. My ram is only 512!I guess for the moment I'd have to stick to Windows one...unless later something simpler comes out or I get a new and more powerful computer!

---

### Post by annietc on 2008-12-15
By the way, for people who wants to view the screenshots, please check this thread that I post. 
[http://ubuntuforums.org/showthread.php?t=1010599](http://ubuntuforums.org/showthread.php?t=1010599)

---

### Post by celticbhoy on 2009-02-11
Getting this when I try and run smile :-

office@office-laptop:~/Desktop/smile$ smile
<-- SMILE QT4.4 VERSION --> 
YOUR LANGUAGE :  "en_GB" 
"LOADING LANGUAGE ... smile_en" 
SYSTEM OVERLAY :  false 
DIRECT RENDERING : TRUE 
DOUBLE BUFFERING : TRUE 
OPENGL SUPPORT : TRUE 
OPENGL VERSION :  15 
smile: ../common/dri_bufmgr_fake.c:594: dri_fake_bo_alloc: Assertion `size != 0' failed.
Aborted
office@office-laptop:~/Desktop/smile$

---

### Post by 4ebees on 2009-02-11
> **celticbhoy said:**
> Getting this when I try and run smile :-

office@office-laptop:~/Desktop/smile$ smile
<-- SMILE QT4.4 VERSION --> 
YOUR LANGUAGE :  "en_GB" 
"LOADING LANGUAGE ... smile_en" 
SYSTEM OVERLAY :  false 
DIRECT RENDERING : TRUE 
DOUBLE BUFFERING : TRUE 
OPENGL SUPPORT : TRUE 
OPENGL VERSION :  15 
smile: ../common/dri_bufmgr_fake.c:594: dri_fake_bo_alloc: Assertion `size != 0' failed.
Aborted
office@office-laptop:~/Desktop/smile$

Hi there,

My best advice would be to post your problem on the SMILE log on the KDE apps site where you downloaded SMILE from. 

The guy who write the application will certainly have an idea about what is going on and he seems quite responsive to posts made on the site.

---

### Post by irishgoth8822 on 2009-07-28
*bump* i tried the instructions in this thread and everything seemed to work, but when i typed 'smile' to run the program, it said 'command not found'.  there is an executable file titled 'smile' in the directory, but double-clicking it merits no response.  any ideas?

---

### Post by nolimit974 on 2009-08-11
I have installed smile using this thread but when i start smile it says that sox is found but with no audio support someone care to help?

---

### Post by 4ebees on 2009-08-11
> **irishgoth8822 said:**
> *bump* i tried the instructions in this thread and everything seemed to work, but when i typed 'smile' to run the program, it said 'command not found'.  there is an executable file titled 'smile' in the directory, but double-clicking it merits no response.  any ideas?

Hi there,
I'm not home at the moment but if you right click on the file, check to see if it is executable (in the tabs that pop up).

Tick executable and see if that helps when you double click on the SMILE file. 

Also you could try (from the command line in the directory housing the SMILE file:

your_machine@someone$./smile 

or ./SMILE (in caps??)

See how you go and get back to us.

---

### Post by 4ebees on 2009-08-11
> **nolimit974 said:**
> I have installed smile using this thread but when i start smile it says that sox is found but with no audio support someone care to help?

Can you post the whole text or a screenshot?

I'm not at home and so will have to check for you later <not saying that I CAN help mind you :)>

---

### Post by 4ebees on 2009-08-11
> **4ebees said:**
> Hi there,
I'm not home at the moment but if you right click on the file, check to see if it is executable (in the tabs that pop up).

Tick executable and see if that helps when you double click on the SMILE file. 

Also you could try (from the command line in the directory housing the SMILE file:

your_machine@someone$./smile 

or ./SMILE (in caps??)

See how you go and get back to us.


Following up on my own post.

Can you do the following in a terminal: 

> 
<name>@<name-desktop>$ sudo updatedb (which means you want to update your database)


Enter the sudo password and then wait until it has finished. Then:

> 
<name>@<name-desktop>$ whereis -b smile 

This should show you were your binary is. It would most likely be here:

> 
/usr/bin/smile


Smile should work it you type:

> 
smile

or

/usr/bin/smile


See if that works if the initial information I gave you does not.

---

### Post by nolimit974 on 2009-08-11
> **4ebees said:**
> Can you post the whole text or a screenshot?

I'm not at home and so will have to check for you later <not saying that I CAN help mind you :)>

here you go

---

### Post by Storyman on 2009-10-14
Smile 1.0 works good for me. Thanks for the help.

---

### Post by 4ebees on 2009-10-15
> **nolimit974 said:**
> here you go

Well, I have absolutely no 'effin' idea what happened there!

I received no message saying that you'd posted anything BUT received a message that Storyman had written. My apologies for that.

If you're still stuck:

It says a 'strange sox' is installed. Did you install Sox directly through the repos or some other way?

Here's a link to a possible solution for the Sox problem.

[http://ubuntuforums.org/showthread.php?t=885201](http://ubuntuforums.org/showthread.php?t=885201)

Can you PM me if you're still following up on this - just so I know you're still working on it or whether you've resolved it.

Thanks and again my apologies for the delay.

---

### Post by rhk on 2009-11-15
I started a IRC channel to discuss Smile. Welcome to join #smile-slideshow

see [http://risto.kurppa.fi/blog/2009/11/two-new-irc-channels-tangogps-and-smile-slideshow/](http://risto.kurppa.fi/blog/2009/11/two-new-irc-channels-tangogps-and-smile-slideshow/) for more information

r

---

