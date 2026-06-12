---
title: "flash player update from adobe"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by angryfirelord on 2007-07-10
Adobe has updated their flash player for Linux. It's at version 9.0.48 [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW")
However, if you try to install the flashplugin-nonfree pacakge from Ubuntu's repos, it won't work because its md5sum checks the old package instead of the new one, so it returns an error and doesn't install. Therefore, you have to install it adobe's way until the deb package has been updated.

---

### Post by Artemis3 on 2007-07-13
Check "details" when installing flashplugin-nonfree:

```
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

This package is now broken in feisty...

---

### Post by Gremlinzzz on 2007-07-13
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
save to desktop
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
:guitar:

---

### Post by Gremlinzzz on 2007-07-13
Let me know if it worked:lolflag:

---

### Post by Gremlinzzz on 2007-07-13
Reason for update
[http://news.zdnet.co.uk/security/0,1000000189,39288022,00.htm](http://news.zdnet.co.uk/security/0,1000000189,39288022,00.htm)

---

### Post by angryfirelord on 2007-07-13
I installed the newer version w/o trouble, however I'm hoping something will make it to the backports.

---

### Post by stchman on 2007-07-13
> **angryfirelord said:**
> Adobe has updated their flash player for Linux. It's at version 9.0.48 [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW")
However, if you try to install the flashplugin-nonfree pacakge from Ubuntu's repos, it won't work because its md5sum checks the old package instead of the new one, so it returns an error and doesn't install. Therefore, you have to install it adobe's way until the deb package has been updated.

I wonder if this new version correct the bug that it covers up drop down menus and some videos that play flash video?

---

### Post by beercz on 2007-07-13
> **Gremlinzzz said:**
> Let me know if it worked:lolflag:
It works!

Thanks Gremlinzzz

---

### Post by stafio on 2007-07-13
The Ubuntu package is ok, but there's a step that needs to be done that keeps the upgrade from working. ```
sudo apt-get --purge remove flashplugin-nonfree
``````
sudo apt-get install flashplugin-nonfree
```That worked for me.

---

### Post by angryfirelord on 2007-07-13
> **stchman said:**
> I wonder if this new version correct the bug that it covers up drop down menus and some videos that play flash video?
Nope, still the same. See for yourself: [http://www.newegg.com/]("http://www.newegg.com/")
I think Adobe said somewhere that they were never going to fix that in version 9 of flash for linux.

---

### Post by beow on 2007-07-14
> **stafio said:**
> The Ubuntu package is ok, but there's a step that needs to be done that keeps the upgrade from working. ```
sudo apt-get --purge remove flashplugin-nonfree
``````
sudo apt-get install flashplugin-nonfree
```That worked for me.

For me too! :popcorn:

---

### Post by abelthorne on 2007-07-14
> **angryfirelord said:**
> Nope, still the same. See for yourself: [http://www.newegg.com/]("http://www.newegg.com/")
I think Adobe said somewhere that they were never going to fix that in version 9 of flash for linux.

I seem to remember that it comes from the implementation of "layers" in Firefox/Gecko that makes Flash applets appear above anything else.
Adobe developers said that they could not fix this behaviour without modifications in Firefox and were working with Mozilla on the problem for a possible fix in Firefox 3.

---

### Post by bla2000 on 2007-07-14
I just tried the 2 commands 

```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

but mine still says at the end:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Also when I run

```
sudo apt-cache policy flashplugin-nonfree
```

It shows:

flashplugin-nonfree:
  Installed: 9.0.31.0.2ubuntu1
  Candidate: 9.0.31.0.2ubuntu1
  Version table:
 *** 9.0.31.0.2ubuntu1 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
        100 /var/lib/dpkg/status

Should I install it from the sources rather than using the flashplugin-nonfree package?

---

### Post by Gremlinzzz on 2007-07-14
Do what works source is just as easy and works for me.use the source luke
:lolflag:

---

### Post by Gabn on 2007-07-15
> **stafio said:**
> That worked for me.

Still failed for me..... 

i'm only getting md5sum problems still maybe my mirror hasn't updated...

---

### Post by Gremlinzzz on 2007-07-15
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

---

### Post by ssmithy on 2007-07-15
> **Gremlinzzz said:**
> Let me know if it worked:lolflag:

Hey, worked liked a champ for me.  Thanks a bunch!  :)

---

### Post by mroy on 2007-07-15
There is an updated deb package of the Flash plugin on Launchpad :

[https://launchpad.net/ubuntu/feisty/i386/flashplugin-nonfree/9.0.48.0.0ubuntu1~7.04.0](https://launchpad.net/ubuntu/feisty/i386/flashplugin-nonfree/9.0.48.0.0ubuntu1~7.04.0)

[https://launchpad.net/ubuntu/+source/flashplugin-nonfree](https://launchpad.net/ubuntu/+source/flashplugin-nonfree)

Works for me...

---

### Post by dougfractal on 2007-07-15
> **stafio said:**
> The Ubuntu package is ok, but there's a step that needs to be done that keeps the upgrade from working. ```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```That worked for me.

Worked for me to.

---

### Post by mroy on 2007-07-15
:!:

---

### Post by Gremlinzzz on 2007-07-15
Good place to check if your flash is working.
[http://www.earthcam.com/](http://www.earthcam.com/)
:guitar:

---

### Post by Gremlinzzz on 2007-07-15
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

WORKED FOR ME:guitar:

---

### Post by angryfirelord on 2007-07-15
Glad to see that no major problems are being reported. I just used the tar.gz and updated flash that way, so now I'm happy. :)

Time to sit back and watch all the lame youtube videos. :popcorn:

---

### Post by Gremlinzzz on 2007-07-16
So utubes working again! was freezing browsers .Think i'll check it out. 
:guitar:

---

### Post by Unicast on 2007-07-16
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

Worked for me. Thanks for that! ;)

---

### Post by Dougie187 on 2007-07-17
Hey guys, This update fixed the menu problem for me. Heres a screenshot for me. I was amazed, just did the sudo commands with Apt-get and it said it didnt update, but i guess it worked fine.

---

### Post by Gremlinzzz on 2007-07-17
need to restart firefox for flash to take effect.
:guitar:

---

### Post by Motomo on 2007-07-18
Gremlinzzz instructions worked perfect for me

---

### Post by angryfirelord on 2007-07-18
Aling with the deb from launchpad, you can also download Gusty's flash with no problems (dependencies are already satisfied on feisty): [http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree]("http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree")

---

### Post by cookies on 2007-07-18
> **Dougie187 said:**
> Hey guys, This update fixed the menu problem for me. Heres a screenshot for me. I was amazed, just did the sudo commands with Apt-get and it said it didnt update, but i guess it worked fine.

That's a Jpeg image now. ;) Not flash.

The menus are only mostly "fixed" in Konqueror for me, look at attachment, some websites still don't work.

---

### Post by Gremlinzzz on 2007-07-19
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

:guitar:

---

### Post by motang on 2007-07-19
Good, finally I was hating the fact that menus would be hidden behind the flash applet.  :-D

---

### Post by octathlon on 2007-07-20
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

 :KS  Thank you soooo much, Gremlinzzz! :D

---

### Post by Gremlinzzz on 2007-07-21
> **octathlon said:**
> :KS  Thank you soooo much, Gremlinzzz! :D

bump 4 next user

---

### Post by jamesstansell on 2007-07-21
This issue is being tracked in bug 125986 [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125986](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125986) and should be in the feisty-proposed repository now.

---

### Post by angryfirelord on 2007-07-22
> **jamesstansell said:**
> This issue is being tracked in bug 125986 [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125986](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125986) and should be in the feisty-proposed repository now.
I still don't understand why it's not in backports by now. All that deb package does is execute a script which fetches the flash player and puts it in the mozilla directory.

---

### Post by NoVista on 2007-07-22
I run Swiftfox here, and I remember at that time  the ONLY way I could get Flash to even work was I had to resort to using Automatix to install the plugins.

How do I install this for Swiftfox?

---

### Post by Gremlinzzz on 2007-07-22
dont know much about Swiftfox but couldnt you just change the folder name command to 
/usr/lib/ swiftfox/plugins if thats where swiftfox keeps its plugins

---

### Post by Gremlinzzz on 2007-07-23
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

:)

---

### Post by NoVista on 2007-07-23
Ok, it syas I have version 9,0,48,0 installed.

BestBuy and MLB, still have the same prob of menus being hidden behing the flash .. ..

---

### Post by CandyMarie596 on 2007-07-25
I am having an interesting time! I attempted to download the 9.0 version tar.gz and as a previous windows user/new linux user I pressed ok right away not really reading. It opened the ark and now i realize I didn't save it so I cannot install it. 

Well, I tried to click the same link on adobe's flash player install page and it is like the link is broken...it does nothing when I click on it...what happened? Can I fix it or is it just a website issue?

Thanks,
Candice

---

### Post by peas on my plate on 2007-07-25
> **Gremlinzzz said:**
> sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
save to desktop
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
:guitar:

amazing.  worked perfectly!

---

### Post by Gremlinzzz on 2007-07-25
> **CandyMarie596 said:**
> I am having an interesting time! I attempted to download the 9.0 version tar.gz and as a previous windows user/new linux user I pressed ok right away not really reading. It opened the ark and now i realize I didn't save it so I cannot install it. 

Well, I tried to click the same link on adobe's flash player install page and it is like the link is broken...it does nothing when I click on it...what happened? Can I fix it or is it just a website issue?

Thanks,
Candice

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by CandyMarie596 on 2007-07-25
Thanks...still didn't pop up the "save to disk" pop up. It is confusing...I will have my friend help. 

Thanks again for your reply

---

### Post by Gremlinzzz on 2007-08-05
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

:guitar:

---

### Post by CandyMarie596 on 2007-08-05
all fixed! yay! It seemed to be a website/browser issue.

---

### Post by Gremlinzzz on 2007-08-08
> **CandyMarie596 said:**
> all fixed! yay! It seemed to be a website/browser issue.

glad too hear it
:guitar:

---

### Post by Gremlinzzz on 2007-08-17
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
:guitar:

:guitar:

---

### Post by angryfirelord on 2007-08-17
If you enable the feisty-proposed repo, you'll automatically get the newest version, allowing you to install flash through apt-get.

---

### Post by Paul133 on 2007-08-17
The newest is 9.0.48.0?

---

### Post by martums on 2007-12-16
> **Gremlinzzz said:**
> sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
save to desktop
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
:guitar:

Thanks  Gremlinzzz!  I've been trying every method I could find, time permitting, since yesterday.  Yours was the first one that worked.  You rock.

Next round is on me.  8-)

---

### Post by angryfirelord on 2007-12-16
The hardy deb package (i386) works fine on gutsy: [http://packages.ubuntu.com/hardy/web/flashplugin-nonfree]("http://packages.ubuntu.com/hardy/web/flashplugin-nonfree")

---

### Post by Llewellyn01 on 2007-12-16
Cheers Gremlinzzz, just did a fresh install on my laptop and wondered if the hardware had failed!

Now all is well with the galaxy!:)

Cheers

Rich

---

### Post by Pengwyn44 on 2007-12-17
> **stafio said:**
> The Ubuntu package is ok, but there's a step that needs to be done that keeps the upgrade from working. ```
sudo apt-get --purge remove flashplugin-nonfree
``````
sudo apt-get install flashplugin-nonfree
```That worked for me.
It did not work for me!

---

### Post by Pengwyn44 on 2007-12-17
I tried this but it did not work. What did work was as follows:
Download the package to Desktop as stated. Then open with 'tar'. The opened package appeared on the Desktop and I right clicked on the opened package and left clicked on 'Open'. Then I restarted the computer and after that I was able to play video clips from the BBC. 
Pengwyn44

---

### Post by wild77 on 2008-02-07
The latest Flash update broke my system today. I was able to fix it by manually installing flash player thanks to this post in another thread.

[http://ubuntuforums.org/showpost.php?p=4276110&postcount=123](http://ubuntuforums.org/showpost.php?p=4276110&postcount=123)

 Why was this included in the automatic updates and was this update not tested before being released?

---

### Post by angryfirelord on 2008-02-07
> **wild77 said:**
> The latest Flash update broke my system today. I was able to fix it by manually installing flash player thanks to this post in another thread.

[http://ubuntuforums.org/showpost.php?p=4276110&postcount=123](http://ubuntuforums.org/showpost.php?p=4276110&postcount=123)

 Why was this included in the automatic updates and was this update not tested before being released?
The reason why it doesn't work is not because the package is technically broken, but because it points to an older version of flash. See, when one downloads the flashplugin-nonfree package, they are not downloading flash itself; flash is being fetched from the adobe server. However, the newest version is a different file size from the older version, which is why you get an MD5 error.

Installing it manually is one method, but the easiest way to fix this issue is to download a deb package from Debian. This one is built for etch and will work on Ubuntu:

[http://http.us.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0.1~etch1_i386.deb]("http://http.us.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0.1~etch1_i386.deb")

---

### Post by fuuma_monou on 2008-02-07
I've been having problems playing Flash videos with the latest plug-in version (9.0.115). Videos will play for a few seconds, then stop, and won't even play back those first few seconds. If I try starting a video, then pause it to let it cache so it won't stutter, nothing gets played back. Now I can't even get the first few seconds. The video player just loads the first frame, then nothing.

---

### Post by gandaran on 2008-02-07
the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) close and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

gandaran

---

### Post by BigSilly on 2008-02-07
> **gandaran said:**
> the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) close and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

gandaran

Installed the Flash "update" today myself, which broke it as reported earlier. Thanks very much gandaran for your useful tips above. Worked like a charm, and I'm back to normal!

Thanks again.

---

### Post by Keith Hedger on 2008-02-07
just installed the update in a 64bit installation and hey presto! my 64bit firefox now plays flash movies!:):)

---

