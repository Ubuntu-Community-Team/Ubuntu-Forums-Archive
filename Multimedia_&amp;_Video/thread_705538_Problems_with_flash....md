---
title: "Problems with flash..."
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by aetherguy881 on 2008-02-23
I'm having a problem with flash on firefox. I can't seem to run all flash applications. Take for an example youtube. I get the standard box for the application but when the video plays it's somewhat distorted. Such that the bottom of the window is cut off and I can't slide through the movie, I also can't change the volume inside the movie or pause and such. Also some of the controls are overlapped...

I have no reason why this is happening, my friend told me to post it here. Also the threads that I found didn't seem to help me...

I'm running Ubuntu Gusty x64.

Thank you.

---

### Post by jeffus_il on 2008-02-23
Do you have the "flashplugin-nonfree" package or the "GPL Flash (SWF) Library" package installed?

---

### Post by aetherguy881 on 2008-02-23
I don't recall doing that...

How would I go about doing it?

---

### Post by Happibun on 2008-02-23
Can I join this thread? I'm looking to install flash in to firefox too, I'm running a 32 bit version of Gutsy.

I've got as far as getting to the Adobe Flash Player Download Center Linux (x86) 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and I can see 3 different flash players 

1 Option 1: .tar.gz
2 Option 2: .rpm
3 Option 3: YUM

But I don't know which is best for me. I downloaded the .tar.gz one but can't work out how to install it through terminal

Quote: 

# Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
# Save the .tar.gz file to your desktop and wait for the file to download completely.
# Unpackage the file. A directory called install_flash_player_9_linux will be created.
# In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

End Quote

Thanks, Jo

---

### Post by gandaran on 2008-02-23
> **Happibun said:**
> Can I join this thread? I'm looking to install flash in to firefox too, I'm running a 32 bit version of Gutsy.

I've got as far as getting to the Adobe Flash Player Download Center Linux (x86) 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and I can see 3 different flash players 

1 Option 1: .tar.gz
2 Option 2: .rpm
3 Option 3: YUM

But I don't know which is best for me. I downloaded the .tar.gz one but can't work out how to install it through terminal

Quote: 

# Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
# Save the .tar.gz file to your desktop and wait for the file to download completely.
# Unpackage the file. A directory called install_flash_player_9_linux will be created.
# In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

End Quote

Thanks, Jo


if you running the 32-bit, why don't you install the flashplugin-nonfree? it's exactly the same adobe flash 9.0.115 ! you'll find it on synaptic and easier to install than the adobe tar.gz. package!

or go to add/remove programs, find the » ubuntu-restricted-extras « and mark for install. this package has everything you'll need, like sun java, adobe flash, codecs and ms fonts.

---

### Post by Happibun on 2008-02-23
> **gandaran said:**
> if you running the 32-bit, why don't you install the flashplugin-nonfree, it's exactly the same adobe flash 9.0.115 ? you'll find it on synaptic and easier to install than the adobe tar.gz. package!

Ok, I'll see if I can find it, Thanks.

That's the thing for Noobs like me just escaped from a windows environment. There's so much choice and it is hard to choose where to begin. I'm a slave to where my search engine takes me. 

	:-k

Jo

---

### Post by wolfen69 on 2008-02-23
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by gandaran on 2008-02-23
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

why you are recommending to uninstall the flash-plugin? the flashplugin-nonfree has been fixed now, it will install the real adobe flash 9.0.115.
this package you recommending to install will work for some people but not all, it still has some bugs.

---

### Post by wolfen69 on 2008-02-23
the .deb package i recommended ***is*** the 9.0.115
getting flash from the repos has been hit or miss as far as flash working right.(no explanation as to why) the file i linked to ***always*** works. i do many installs of ubuntu, that's how i know these things. i also do computer work for a living. have a nice day.

---

### Post by gandaran on 2008-02-23
> **wolfen69 said:**
> the .deb package i recommended ***is*** the 9.0.115
getting flash from the repos has been hit or miss as far as flash working right.(no explanation as to why) the file i linked to ***always*** works. i do many installs of ubuntu, that's how i know these things. i also do computer work for a living. have a nice day.

I did try this package in january when the flashplugin-nonfree in synaptic was broken, it didn't work for me and I also read many post's here with many people saying the same! I had to install the adobe tarball , which I deleted now and installled the flashplugin-nonfree, this package was fixed about two weeks ago, there's absolutely no problem now with the flashplugin-nonfree now.

---

### Post by wolfen69 on 2008-02-23
if you install the ubuntu restricted extras i found there is a chance that the flash included will not work. 3 installs on 3 seperate computers(within the last 2 weeks) has confirmed this. my .deb flash method worked though. your mileage may differ. peace.

---

### Post by aetherguy881 on 2008-02-23
The link provided had the wrong architecture for me and I do have the flash installed in the repo.  I have tried that tar.gz file but haven't been able to get it to work...

---

### Post by gandaran on 2008-02-24
aetherguy881

the adobe tar.gz file is for 32-bit systems, there isn't  a 64-bit flash, you'll have to stick to the flashplugin-nonfree in the 64-bit systems repo's, which is a special package prepared for 64-bit, unfortunately it seems it is still a 
broken package (only the 32-bit flashplugin-nonfree has been repaired) 

to find out if it has been repaired you'll have to uninstall the flashplugin-nonfree (use synaptic, choose complete removal, then update synaptic » sudo apt-get update «) then reinstall the same flashplugin.

there are other ways to make flash work on 64-bit.
there is a work around I believe (I don't use the 64-bit, so I don't know exactly how it's done) but I think it's a combined use of flash and nspluginwrapper.  
another way, you can install a 32-bit firefox and use the same firefox to install flash in the home .mozilla plugins folder.

or you could try the opera browser, download the opera 2.50b (attention here on detail, ubuntu 7.10 .deb package 2.50b version) from the opera site.
to install flash, download the adobe tarball, unpack and place the libflashplayer.so file in a folder (rename the folder » plugins «) copy that plugins folder to  your home/user/ .opera folder. it's very simple.

---

### Post by aetherguy881 on 2008-02-27
I updated the repo and it didn't fix anything. I'll try the other potential solutions once I get more time...

Long MATLAB assignments are crippling for time.

Thanks

---

### Post by iheartubuntu on 2008-02-27
> **wolfen69 said:**
> the .deb package i recommended ***is*** the 9.0.115
getting flash from the repos has been hit or miss as far as flash working right.(no explanation as to why) the file i linked to ***always*** works. i do many installs of ubuntu, that's how i know these things. i also do computer work for a living. have a nice day.

You sound very knowledgeable! Im having problems getting sound in any flash player to work. I can watch WMVs that are embedded and I get sound everywhere else on my computer, but no sound with flash videos from youtube, msnbc, etc. Any tips? I started a thread here but no replies.

[http://ubuntuforums.org/showthread.php?t=708405](http://ubuntuforums.org/showthread.php?t=708405)

Many thanks! Its really frustrating. Ive got Ubuntu on 3 other computers and sound works great.

---

### Post by ellalan on 2008-03-08
I did have the same problem and I found a link you may give it a try.
You have to uninstall the Flash plugin-nonfree already inthe Snaptic, then follow the instructions to install Adobe Flashplayer9.

[www.psychocats.net/ubuntu/flashmanual](www.psychocats.net/ubuntu/flashmanual)
It worked for me and I HTH.

---

