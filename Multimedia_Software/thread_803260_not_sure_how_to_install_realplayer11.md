---
title: "not sure how to install realplayer11"
date: 2008-05-22
forum: Multimedia Software
---

### Post by bsg221 on 2008-05-22
hey new to linux having a bit of trouble trying to install real player 11
can any one hep please and thank you

---

### Post by itix on 2008-05-22
Ouch... this is a rather painful procedure since real player didn't bother packaging it :(

I'll help you to the extent of my knowledge.

Download the real player 11 .bin file (I think Firefox defaults it to the desktop).

Go to *Applications => Accessories => Terminal* and type *cd Desktop* and hit enter (this will navigate the terminal to your desktop). 
Then type *sudo chmod a+x* and then drag your file to the terminal. Revove the path ("/home/username/ etc) but leave "sudo", "chmod", "a+x" and the file name, then hit enter. After that, press up-arrow and erase "chmod a+x" and type ./ so that it looks like "sudo ./filename" and follow the on screen instructions. A good path to install it in is /usr/share which is a global binary folder.

---

### Post by bigken on 2008-05-22
you might have to right click the file 1st to make it executable

---

### Post by Fenris_rising on 2008-05-22
follow this to the letter. it sorted mine out no problem. its aimed at FF3 beta as it comes with hardy. if you have FF2 dont do anything from point 3 onwards. not my own work btw but i saved the info for reference. 

m to work on Ubuntu 8.04 Hardy Heron
April 27, 2008 - 22:49 — webmaster 

Raaga.com is a very popular online music station that has a very large collection of Indian movie and classical songs. They use real media and they have a player that requires the real media player. Now the default installation of Real Media player will not allow you play music from Raaga.com and the player popup from raaga.com will stay in the 'Initializing player, Please Wait' and 'Loading' state permanently. There is a simple work around for this situation.
All you have to do is to follow these simple instructions.
1) Download the latest Realplayer from the HelixCommunity.org or from Real.com. We had tested with RealPlayer11Gold.bin. Remember it is the Realplayer and not the Helix Player. The file that we had downloaded and tested was

[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin). When prompted save the file to your home folder

2) Set the executable bit of the file and then run the installer.

chmod +x RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin

Proceed with the installation and leave the default options as they are. If all goes well your Real Player will be installed to /opt/real/RealPlayer.
========================================================================= 
3) However there has been some directory level changes with Firefox 3 which comes with Ubuntu 8.04 and hence the Real Player plugin will not work in Firefox. You can easily fix this problem by running the following commands

cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

Now check if the Real Player plugin is installed properly by typing in the following in the Firefox address bar - about:plugins. If you had followed the instructions correctly and you have Ubuntu 8.04 and have used Real Player 11 Gold you should be able to see the following in the about:plugins page

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
File name: /usr/local/RealPlayer/mozilla/nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.626 built with gcc 3.2.0 on Jul 26 2007

4) Now go to raaga.com and see if the player is working. It should be. Have fun.
If you face any problem while setting up the player or getting it to work, do post your questions as comments and we will try to help you.

---

### Post by bsg221 on 2008-05-22
hey thank alot guys i owe you all big 
much

---

### Post by itix on 2008-05-22
I'll presume that means it worked =p

---

### Post by cowbuntu on 2008-06-03
We do realise that the embedded player needs work for the Firefox 3 release and will be working on getting the plugins in the correct locations as well as some additional bug fixes very soon.

-RealPlayer QA for Linux.

---

### Post by Skillachi on 2008-06-03
Itix i followed your instructions to the T. Installed it to /usr/share and everythign hwoever now i get an error:

Could not launch Menu item

failed to execute the child process "/usr/bin/realplay" permission denied...

How do i fix that error

---

### Post by dupersuper on 2008-06-03
> **cowbuntu said:**
> We do realise that the embedded player needs work for the Firefox 3 release and will be working on getting the plugins in the correct locations as well as some additional bug fixes very soon.

-RealPlayer QA for Linux.

cool that theres people from real here :guitar:
could we have pulseaudio support too :lolflag:

---

### Post by itix on 2008-06-04
huh?? That means you're not th owner of the binary for some strange reason. Go to the terminal and type *[COLOR="Green"]cd /usr/share/[/COLOR]* and then type *[COLOR="Green"]ls[/COLOR]*. In the list that appears, try to locate the real player folder. After having done so, type [COLOR="Green"]sudo chown -R [COLOR="Navy"]your-user-name whatever-folder-was-called[/COLOR][/COLOR]. 

Let me give you an example. My user name is *itix*, and lets say real player installed itself in a folder named *pumpkin*. I must then type [COLOR="Green"]sudo chown -R itix pumpkin[/COLOR].

The command lines I gave you changes dirctory of the terminal to /usr/share (*cd /usr/share*) and then lists the available items (*ls*). *sudo chown -R* means "as root, change ownership to the user specified including subfolders and files".

---

### Post by SidF on 2008-06-05
Hi All. I'm trying to do the same thing and am a Ubuntu newbie. I have FF 7.04 64 bit that came preinstalled on the machine I bought. I chose /opt as the directory  to install RealPlayer in and now I get a message that says: Failed to execute child process realplay, no such file or directory. Should I have chosen usr or some other directory like /etc? Will this version of RealPlayer( RealPlayer11GOLD.bin) work with 64 bit Feisty Fawn or only 32 bit? I'm trying to listen to the UK BBC radio and it needs RealPlayer to do this apparently.
Thanks in advance for any help you can give. I'm interested in getting some Linux skills and this sort of problem solving is a good way to find out how things work,or don't work as in this case.

---

### Post by Skillachi on 2008-06-05
itix i still am running into the same problems... should i do a re-install and then let it go back to whatever defaults it wanted?

---

### Post by itix on 2008-06-06
SidF:

There are other programs than real player that can handle real player formats on linux. You don't need the real player-player unless you absolutely love its UI or something. I suspect it being problems with the architecture if I must be honest. Try looking for a 64-bit compatible real media player.

Skillachi:

I personally don't use real player, so I can't check exactly what's wrong but I don't get why you get problems even after having changed owner. Are you sure that it is EXACTLY the same problem? That means chown failed to change the ownership to your user...

Try this instead: *[COLOR="Green"]sudo nautilus[/COLOR]* (or if you have xubuntu; *sudo thunar* or kubuntu; *sudo konqueror*). Then go to the folder above the install folder (file system => usr => share), right click on the  install folder (which is probably called realplayer or something, and choose properties. Go to the permissions tab and check who owns the folder. If it says anything other than your user, change it to your user. Then check the content of the folder and if they are owned by anything other than your user, change them too. It's a rather slow and tedious way, but it SHOULD work.

If all files and folder were owned by your user, something's seriously strange. In that case, I'd just reinstall it in a folder in my home folder in a folder called "programs" or something like that.

---

### Post by agamotto on 2008-06-06
You would honestly be better off without RealPlayer.  I replaced realplayer with VLC media player nearly two years ago, and I don't miss it at all.

---

### Post by Skillachi on 2008-06-07
I really need realplayer because my phone saves files in 3gp format, and vlc doesn't play them with sound... i just see video and not sound. So i want something to play the files with and realplayer is the only player that does that. Unless there is a quicktime for this situation and im not really sure that quicktime plays these files well either i've only heard.

---

### Post by itix on 2008-06-07
Did you follow my instructions above? If so, please tell me the result ;)

---

### Post by Sealbhach on 2008-06-07
I have the same problem, I looked at the file in nautilus, here's what it looks like:

[http://i32.tinypic.com/10eed5v.png](http://i32.tinypic.com/10eed5v.png)

It's annonying being told I'm not the owner. I'm the only person who uses this machine. :(

.

---

### Post by darkaudit on 2008-06-08
> **agamotto said:**
> You would honestly be better off without RealPlayer.  I replaced realplayer with VLC media player nearly two years ago, and I don't miss it at all.

I use VLC no matter the platform. Unfortunately, .rm files aren't supported by VLC. Suggestions if Realplayer or Helix are to be avoided?

---

### Post by itix on 2008-06-08
Ooops, double post... sry

---

### Post by itix on 2008-06-08
> **Sealbhach said:**
> I have the same problem, I looked at the file in nautilus, here's what it looks like:

[http://i32.tinypic.com/10eed5v.png](http://i32.tinypic.com/10eed5v.png)

It's annonying being told I'm not the owner. I'm the only person who uses this machine. :(

.

Did you really use [COLOR="Green"]***sudo** nautilus*[/COLOR] ??
If i go to the terminal and type *[COLOR="Green"]sudo nautilus[/COLOR]*, I am able to change the files ownership...

Like this:
[[IMG]http://img514.imageshack.us/img514/9638/screenshotdocumentspropof8.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshotdocumentspropof8.png)

---

### Post by Sealbhach on 2008-06-11
> **itix said:**
> Did you really use [COLOR="Green"]***sudo** nautilus*[/COLOR] ??
If i go to the terminal and type *[COLOR="Green"]sudo nautilus[/COLOR]*, I am able to change the files ownership...


Oh, Ok, didn't know about 

sudo nautilus

Thanks.


.

---

### Post by Skillachi on 2008-06-11
I tried the sudo nautilus thing... still nothing. Now the msg says
"Details: failed to execute child"
process "realplay" (permission denied)

*sigh* im gonna cry.... So how do i do the whole uninstall thing now? (yes i'm a noob)

---

### Post by Akhlies on 2008-06-14
sorry guys  i  don't know  how  playe any movie in youtube.com .also i ma new user  for ubuntu 7.10 flashplayer  already installed in my synaptic package i  don't know  what can i  do  and what's the terminal command  to install flashplayer and reaplayer 11  . please  step by step thanks all:(:(

---

### Post by chillyair on 2008-06-16
Ok I'm running 64 bit hardy and am having almost the exact same problems that have been posted here. So far i've found nothing to resolve the problem but I have the realplayer link showing up in my applications menu (even though it won't open). Does anyone know how I can uninstall it? I'm fairly new to linux so if it doesn't show up in synaptic or add/remove I don't know how to get rid of it.

---

### Post by oldos2er on 2008-06-16
> **Akhlies said:**
> sorry guys  i  don't know  how  playe any movie in youtube.com .also i ma new user  for ubuntu 7.10 flashplayer  already installed in my synaptic package i  don't know  what can i  do  and what's the terminal command  to install flashplayer and reaplayer 11  . please  step by step thanks all:(:(

 See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

