---
title: "FLASH-AID: remove conflicting plugins and install proper flash plugin version"
date: 2010-05-23
forum: Multimedia Software
---

### Post by lovinglinux on 2010-05-23
Flash issues are very common and threads asking for help are posted several times a week. 

In order to provide an easy solution for new users to install Flash and solve some common issues, I have created [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/flash-aid), which is a Firefox extension that automates the process of removing conflicting plugins and installing the proper version of Flash according to browser architecture.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid)

[[IMG]http://www5.picturepush.com/photo/a/5794338/640/5794338.jpg[/IMG]](http://picturepush.com/public/5794338)

---

### Post by lovinglinux on 2010-05-23
I had to release version 1.0.1 to fix a bug if you install the 32bit version on a 64bit machine. Links on the first post are updated.

If you have a 32bit version and it doesn't install properly, grab the new version too.

Sorry for the inconvenience.

---

### Post by Superluke on 2010-05-30
I have been having a real problem getting flash working since trying to install the 64-bit version.  I'm running 10.04 x64 and 64-bit Firefox 3.6.3 ... whatever I do I can't get it to recognize the plugin.  Flash-aid tells me that I'm running 32-bit architecture and tries to install the 32-bit plugin... which doesn't work.  Whatever I do I get the message saying "plugin required" ... and "about:plugins" says none are installed.

---

### Post by lovinglinux on 2010-05-30
> **Superluke said:**
> I have been having a real problem getting flash working since trying to install the 64-bit version.  I'm running 10.04 x64 and 64-bit Firefox 3.6.3 ... whatever I do I can't get it to recognize the plugin.  Flash-aid tells me that I'm running 32-bit architecture and tries to install the 32-bit plugin... which doesn't work.  Whatever I do I get the message saying "plugin required" ... and "about:plugins" says none are installed.

Could you please click "Help >> About Firefox", take a screenshot of that window and post it here?

Also please post the output of these commands:

```
uname -a
```

```
locate libflashplayer.so
```

---

### Post by Superluke on 2010-05-30
About Firefox:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

uname -a:

Linux luke-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

locate libflashplayer.so shows it wherever I put it.... the /plugins directories...

---

### Post by Superluke on 2010-05-30
/home/luke/.limewire/browser/xulrunner/plugins/libflashplayer.so
/home/luke/.limewire/browser/xulrunner/plugins/npwrapper.libflashplayer.so
/home/luke/.mozilla/plugins/libflashplayer.so
/home/luke/.mozilla_backup_2009-10-15T12:59:55-0400/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> About Firefox:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

uname -a:

Linux luke-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

locate libflashplayer.so shows it wherever I put it.... the /plugins directories...

Thanks. I will upload a new version in a couple of minutes that should fix the architecture detection and allow you to install the 64bit flash. The fix is already in place, I just need to upload it to the mozilla server.

BTW, how did you install Firefox?

---

### Post by lovinglinux on 2010-05-31
[Version 1.0.3 is available for download](http://flash-aid-extension.blogspot.com/).

Please tell me know if it works for you.

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> [Version 1.0.3 is available for download]("http://flash-aid-extension.blogspot.com/").

Please tell me know if it works for you.

It does detect the correct version now (Progress!) but I still get the "install missing plugins" message and I still show nothing under "about:plugins" ...

I've installed Firefox a few different ways (I *am* worried that there might be traces of other installations hiding around...) but the latest is just 3.5.3 from the repositories.  I had installed "Namoroka" (the development version) and for whatever reason my launcher still says that but I don't *think *it's still on here anywhere :(

I'm sure I've screwed it up mainly by trying different scripts and such that I've found around the web... just like I tend to do with my audio configuration (Which is still messed up too!)

Thanks for your help!

Edit: I can't seem to get Firefox to recognize ANY plugins... whatever I try to add asks me to install it, then says it's already installed.

---

### Post by akakingess on 2010-05-31
Thank you, it worked perfectly for me, and now I have the correct version and 64-bit version installed!! Thanks for taking the hassle out of probably the only thing that I have found 'annoying' (for lack of a better word), it's because of people like you that more and more will come to love Ubuntu/Linux!  Good work and thanks again.

---

### Post by lovinglinux on 2010-05-31
> **akakingess said:**
> Thank you, it worked perfectly for me, and now I have the correct version and 64-bit version installed!! Thanks for taking the hassle out of probably the only thing that I have found 'annoying' (for lack of a better word), it's because of people like you that more and more will come to love Ubuntu/Linux!  Good work and thanks again.

You are welcome.

---

### Post by bapoumba on 2010-05-31
[http://ubuntuforums.org/showthread.php?p=9389623](http://ubuntuforums.org/showthread.php?p=9389623)

Several posts moved out from this thread to its own :)

---

### Post by lovinglinux on 2010-05-31
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?p=9389623](http://ubuntuforums.org/showthread.php?p=9389623)

Several posts moved out from this thread to its own :)

Thank you.

---

### Post by lovinglinux on 2010-06-02
Version 1.0.3 of FLASH-AID has been approved by Mozilla and is now available through the Stable Channel. Future versions updates will be available through Firefox add-ons manager.

---

### Post by cchhrriiss121212 on 2010-06-03
This is a good extension, so thanks. However, the update process today required me to reinstall the plugins instead of upgrading them, is this normal? I'm using 32bit.

---

### Post by lovinglinux on 2010-06-03
> **cchhrriiss121212 said:**
> This is a good extension, so thanks. However, the update process today required me to reinstall the plugins instead of upgrading them, is this normal? I'm using 32bit.

Yes. It is essentially the same as upgrading, the only difference is that the process used by the extension makes sure that there is no left-overs from previous installations. Lots of users perform several different installation methods while trying to make flash work that can leave traces behind and cause conflicts. So the extension remove the packages to make sure you have only the necessary ones.

---

### Post by lovinglinux on 2010-06-04
Version 1.0.4 of the extension has been released and brings the following changes:

[LIST]
[*]fixed toolbar button
[*]added missing symlink on 32bit installs
[*]added visual confirmation before running the install script
[*]install script is now non-interactive
[*]added option to install flash 32bit 10.1rc7
[/LIST]

Automatic updates through Firefox add-ons manager will be offered when Mozilla approves it, which should take about a week. Nevertheless, this version can be downloaded and installed directly from the  Stable Channel on the extension site.

Beta Channel users will be offered to upgrade automatically to version 1.0.4rc, which is the final version.

---

### Post by kaonashi on 2010-06-04
I finally registered on these forums so I could commend you on your awesome flash extensions. Flash-Aid and FlashVideoReplacer have remedied all my flash woes.

---

### Post by lovinglinux on 2010-06-04
> **kaonashi said:**
> I finally registered on these forums so I could commend you on your awesome flash extensions. Flash-Aid and FlashVideoReplacer have remedied all my flash woes.

Thank you for registering here and posting your comment. I really appreciate it.

:popcorn:

---

### Post by cchhrriiss121212 on 2010-06-07
> Yes. It is essentially the same as upgrading, the only difference is that the process used by the extension makes sure that there is no left-overs from previous installations. Lots of users perform several different installation methods while trying to make flash work that can leave traces behind and cause conflicts. So the extension remove the packages to make sure you have only the necessary ones.
I see what you mean, but it seems redundant to do this twice, as it had already done this process once when I installed and again when the upgrade came out. It doesn't bother me that much, it is just a case of having to hit yes 3 times instead of once.

Unless you think people are going to try different installations after installing this plugin? Which would be unusual of them as it seems to work nicely.

---

### Post by lovinglinux on 2010-06-07
> **cchhrriiss121212 said:**
> I see what you mean, but it seems redundant to do this twice, as it had already done this process once when I installed and again when the upgrade came out. It doesn't bother me that much, it is just a case of having to hit yes 3 times instead of once.

Unless you think people are going to try different installations after installing this plugin? Which would be unusual of them as it seems to work nicely.

If the upgrade doesn't include a new version of flash or if you are happy with your installation you can simply ignore the automatic execution and close the dialog. I'm going to work on a better method for upgrades. BTW, in the newest version, which hasn't been approved by Mozilla yet, the script is non-interactive. Before executing the script, the extension display the code to be executed, so you can read it and cancel. But once started, the script will execute without intervention.  There is no need to type "y" 3 times anymore. Please let me know what you think about it.

---

### Post by lovinglinux on 2010-06-11
A [critical vulnerability](http://www.adobe.com/support/security/advisories/apsa10-01.html) has been identified a couple of days ago and Adobe is recommending the upgrade to version 10.1. Nevertheless, this version is not available in Ubuntu repositories yet and will not be available for 64bit users.

I will release a new version of FLASH-AID as soon as Ubuntu updates the repositories and will remove support for flash 64bit entirely. Unfortunately, the 64bit version is no longer being supported by Adobe.

---

### Post by PinchedNerve on 2010-06-11
So is it suggested to go to the 32bit version of flash on x64 systems?

---

### Post by Nocia on 2010-06-11
At first thanks a lot for this nice plug'in!

Since I installed it I have a problem with Zattoo (a very popular free TV player). Zattoo uses flash player so I put it in its lib directory as it is explained on the Ubuntu website :
ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/zattoo/

However Zattoo said it doesn't have flash player installed. With the previous version (flash plugin installer from synaptic) the player was working.

So do you think it is because Zattoo doesn't support flash player 64 bits? Is there some differences for an external program? Do you know a solution?

Thanks a lot in advance for any help.

Nocia

---

### Post by lovinglinux on 2010-06-11
> **PinchedNerve said:**
> So is it suggested to go to the 32bit version of flash on x64 systems?

Unfortunately yes. Nevertheless, the version available in the repositories is still 10.0.45.2 at this moment. The new version of flash has already been accepted in the backports repository and should be available soon.

> **Nocia said:**
> So do you think it is because Zattoo doesn't support flash player 64 bits? 

Probably, because it should detect the player after creating the symlink with that command. Have you tried to re-create the symlink?

> **Nocia said:**
> Do you know a solution?

Reinstall the 32bit version.

---

### Post by lovinglinux on 2010-06-11
FLASH-AID 1.0.5 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.5rc, but it is identical to the final version. Beta Channel users can update through Firefox Add-on manager now.

This version brings the new flash 10.1 and removes the support for 64bit version installation, due to the fact that Adobe is no longer releasing flash for 64bit and all available versions have a critical vulnerability. Nevertheless, 64bit users will be able to install the 32bit version, which uses nspluginwrapper.

You should update the extension and install the new flash version as soon as possible.

---

### Post by xzero1 on 2010-06-11
> **lovinglinux said:**
> FLASH-AID 1.0.5 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.5rc, but it is identical to the final version. Beta Channel users can update through Firefox Add-on manager now.

This version brings the new flash 10.1 and removes the support for 64bit version installation, due to the fact that Adobe is no longer releasing flash for 64bit and all available versions have a critical vulnerability. Nevertheless, 64bit users will be able to install the 32bit version, which uses nspluginwrapper.

You should update the extension and install the new flash version as soon as possible.

I have installed and run flash-aid 1.0.5 on Lucid 64-bit but the flash version reports 10.0.45.2!:confused:

---

### Post by lovinglinux on 2010-06-11
> **xzero1 said:**
> I have installed and run flash-aid 1.0.5 on Lucid 64-bit but the flash version reports 10.0.45.2!:confused:

You are probably using a mirror sever that hasn't been updated with this morning changes. See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by corrytonapple on 2010-06-12
Were do I find this version? I get it from [here.]("http://get.adobe.com/flashplayer/otherversions/") I open  it with "apturl" (default) and it says downloading, then it gives the  error (attached) "package 'adobe-flashplugin' is virtual. Where do I  find the latest Flash player plug-in from adobe that will work? I use a  64-bit system.

---

### Post by lovinglinux on 2010-06-12
> **corrytonapple said:**
> Were do I find this version? I get it from [here.]("http://get.adobe.com/flashplayer/otherversions/") I open  it with "apturl" (default) and it says downloading, then it gives the  error (attached) "package 'adobe-flashplugin' is virtual. Where do I  find the latest Flash player plug-in from adobe that will work? I use a  64-bit system.

Run this command:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by xzero1 on 2010-06-12
> **lovinglinux said:**
> You are probably using a mirror sever that hasn't been updated with this morning changes. See [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

This morning's update installed 10.1.53.64. Thanks.

---

### Post by blacksunseven on 2010-06-12
Just wanted to chime in and say that both the stable and beta release installed and functioned flawlessly for me in 64-bit Lucid. It, of course, had to install 32-bit Flash with ndiswrapper because Adobe is a bunch of ... well, everyone knows. Anyways, let's hope Adobe gets their act together (lol here if you want) and gets back on track with a 64-bit version of Flash... For now I'm having to hoard my 10.0.x version of 64-bit so Hulu functionality isn't broken.

---

### Post by Nocia on 2010-06-13
Yes I have already tried to recreate the symlink...
Although the Zattoo rich client doesn't work, using the online web client within Firefox works perfectly (maybe in this case this is Firefox that verifies the flash version).
So for the WorldCup it's sufficient.

Thanks for your help and good luck to the Brazil!

---

### Post by lovinglinux on 2010-06-13
> **Nocia said:**
> Yes I have already tried to recreate the symlink...
Although the Zattoo rich client doesn't work, using the online web client within Firefox works perfectly (maybe in this case this is Firefox that verifies the flash version).
So for the WorldCup it's sufficient.

Thanks for your help and good luck to the Brazil!

Good luck to your team too.

---

### Post by lovinglinux on 2010-06-13
For those having issues when clicking flash controls while using the 32bit plugin running on a 64bit browser, try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by corrytonapple on 2010-06-13
Thanks, your plug-in worked!:guitar:

---

### Post by no2498 on 2010-06-13
im on 804 32 bit got the update yesterday it killed all 3 of my browsers  
went back to flash 9 sorry

---

### Post by cj.surrusco on 2010-06-19
I have 64-bit Ubuntu with 64-bit Firefox. I had the flash configuration set up and it was working pretty well, there we're no problems in Youtube and the only problems that I had were on websites that I do not visit very frequently. 

I hoped that the Flash Aid plugin would solve these few problems, but it in fact made it worse. 

I started the plugin and it informed me that it would install the 32-bit version even though I was running 64-bit. I allowed it do so, and it says that it finished succesfully.

However, now flash barely works anywhere. Youtube, for example, will not play/pause and the other options won't work either

Can you please give me some instruction on how to reverse the effects of the plugin?

---

### Post by Sapienso on 2010-06-19
Thanks a lot, lovinglinux. 

I had this problems since I installed ubuntu Lucid Linx. 

I used your tool, and it worked perfectly. 

Thanks again. Very useful for people like me, who love linux (as you do :)), but who are only final users, not very handy with shell commands.

---

### Post by lovinglinux on 2010-06-19
> **cj.surrusco said:**
> I have 64-bit Ubuntu with 64-bit Firefox. I had the flash configuration set up and it was working pretty well, there we're no problems in Youtube and the only problems that I had were on websites that I do not visit very frequently. 

I hoped that the Flash Aid plugin would solve these few problems, but it in fact made it worse. 

I started the plugin and it informed me that it would install the 32-bit version even though I was running 64-bit. I allowed it do so, and it says that it finished succesfully.

However, now flash barely works anywhere. Youtube, for example, will not play/pause and the other options won't work either

Can you please give me some instruction on how to reverse the effects of the plugin?

The extension installed the 32bit plugin because Adobe is no longer supporting the 64bit and ALL currently available versions have a critical vulnerability. You shouldn't use the 64bit version anymore, at least until the provide a new version. When they do, I will provide it again with FLASH-AID.

Meanwhile, you can fix you problem doing the following:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

> **Sapienso said:**
> Thanks a lot, lovinglinux. 

I had this problems since I installed ubuntu Lucid Linx. 

I used your tool, and it worked perfectly. 

Thanks again. Very useful for people like me, who love linux (as you do :)), but who are only final users, not very handy with shell commands.

You are welcome.

---

### Post by cj.surrusco on 2010-06-19
> **lovinglinux said:**
> 
Meanwhile, you can fix you problem doing the following:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

I tried that fix and it didn't work the first time I restarted Firefox, but it worked after restarting my computer!

Thanks a lot for the tip!

---

### Post by tnt533 on 2010-06-25
Thank you! I had the same issues as this guy with controls on youtube.com not being accessable which led me to this thread. I added the code you suggested to my npviewer file and everything is great.

Lets hope Adobe fixes the issues with the 64bit version of their plugin so we can stop having to run 32bit libraries on our 64bit systems!

> **lovinglinux said:**
> The extension installed the 32bit plugin because Adobe is no longer supporting the 64bit and ALL currently available versions have a critical vulnerability. You shouldn't use the 64bit version anymore, at least until the provide a new version. When they do, I will provide it again with FLASH-AID.

Meanwhile, you can fix you problem doing the following:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.



You are welcome.

---

### Post by Saint Aardvark on 2010-07-03
One more thank-you from me..."export GDK_NATIVE_WINDOWS=1" did the trick!

---

### Post by Yellow Pasque on 2010-07-03
> **Superluke said:**
> About Firefox:

Mozilla/5.0 (X11; U; Linux **[SIZE="4"]i686[/SIZE]** (x86_64); en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

If you're running 64-bit Ubuntu and you see i686 in your browser string, you've managed to (probably unintentionally) install a 32-bit browser (which would need 32-bit plugins in /usr/lib32).

---

### Post by lovinglinux on 2010-07-13
FLASH-AID 1.0.6 was released today and is available for download through the [Stable Channel](http://flash-aid-extension.blogspot.com). It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.6rc, but it is identical to the final version.

This version fixes one bug that was affecting 32bit systems and another bug that was affecting Portuguese systems. See [Changelog](http://flash-aid-extension.blogspot.com/p/changelog.html) for details.

---

### Post by lovinglinux on 2010-07-14
FLASH-AID 1.0.7 was released today and is available for download through the [Stable Channel](http://flash-aid-extension.blogspot.com). It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.7rc, but it is identical to the final version.

This version adds an option to only remove flash (feature request) and adds compatibility with Firefox 4.0b2pre. There are other important changes in the version released yesterday. See [Changelog](http://flash-aid-extension.blogspot.com/p/changelog.html) for details.

---

### Post by lovinglinux on 2010-07-19
[FLASH-AID 1.0.8](http://flash-aid-extension.blogspot.com) was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.8rc, but it is identical to the final version.

This version just fixed a minor issue introduced by version 1.0.7, that prevents the automated installer from pop up on new installations of the extension. The flash installation feature still can be performed on version 1.0.7 through the status bar launcher or the toolbar launcher. See [Changelog](http://flash-aid-extension.blogspot.com/p/changelog.html) for details of other changes since version 1.0.6;

---

### Post by lovinglinux on 2010-07-21
FLASH-AID 1.0.9 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.9rc, but it is identical to the final version.

This version just adds compatibility with Firefox 4.0b3pre.

---

### Post by lovinglinux on 2010-07-26
FLASH-AID 1.0.10 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.10rc, but it is identical to the final version.

This version fixes a bug with automatic launcher and added button to toolbar automatically.

---

### Post by lovinglinux on 2010-08-18
FLASH-AID 1.0.11 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.11rc, but it is identical to the final version.

This version adds multi-user support and also lightspark plugin removal.

---

### Post by Alver on 2010-09-06
> **kaonashi said:**
> I finally registered on these forums so I could commend you on your awesome flash extensions. Flash-Aid and FlashVideoReplacer have remedied all my flash woes.
I wish I could say the same! I'm running Ubuntu 10.4.1 64 b/W7 64 b in dual boot mode on a Toshiba L 505-10M and Ubuntu has very few hick-ups. Alas Flash Player is one of them. I'm trying to follow "Mi vida loca" (Spanish lessons on BBC) using Firefox 3.6.8. I have installed the above mentioned plugins but it is not possible to see the video's of the lessons series. I have to use Windows 7, also with Firefox, and there I can follow the complete programme with all the video episodes. Any suggestions on how to remedy this would be most welcome.

Alver

---

### Post by lovinglinux on 2010-09-06
> **Alver said:**
> I wish I could say the same! I'm running Ubuntu 10.4.1 64 b/W7 64 b in dual boot mode on a Toshiba L 505-10M and Ubuntu has very few hick-ups. Alas Flash Player is one of them. I'm trying to follow "Mi vida loca" (Spanish lessons on BBC) using Firefox 3.6.8. I have installed the above mentioned plugins but it is not possible to see the video's of the lessons series. I have to use Windows 7, also with Firefox, and there I can follow the complete programme with all the video episodes. Any suggestions on how to remedy this would be most welcome.

Alver

Please provide a link to the video page.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Alver on 2010-09-07
> **lovinglinux said:**
> Please provide a link to the video page.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

Hello lovinglinux, thx for speedy and elaborate reply. I have treid to follow your instructions as best as I understand them. Here we go:
BBC website:
[http://www.bbc.co.uk/languages/spanish/mividaloca/](http://www.bbc.co.uk/languages/spanish/mividaloca/)
For your other instructions please, see the attached files. I took me a while to get the firefox.txt output. I'm running a Dutch language version and the commands only gave an output when I replaced "Desktop" with the dutch equivalent "Bureaublad". I hope you will be able to use this info.

Alver

---

### Post by lovinglinux on 2010-09-07
> **Alver said:**
> Hello lovinglinux, thx for speedy and elaborate reply. I have treid to follow your instructions as best as I understand them. Here we go:
BBC website:
[http://www.bbc.co.uk/languages/spanish/mividaloca/](http://www.bbc.co.uk/languages/spanish/mividaloca/)
For your other instructions please, see the attached files. I took me a while to get the firefox.txt output. I'm running a Dutch language version and the commands only gave an output when I replaced "Desktop" with the dutch equivalent "Bureaublad". I hope you will be able to use this info.

Alver

There is nothing wrong with your report, except that you have a third-party ppa repository installed. Try to disable the sevenmachines ppa from "System >> Software Sources >> Other Software" then run FLASH-AID again. There is an icon in Firefox statusbar and nav toolbar, that allows to run it again.

What kind of error do you get on the BBC language site?

---

### Post by Alver on 2010-09-07
> **lovinglinux said:**
> There is nothing wrong with your report, except that you have a third-party ppa repository installed. Try to disable the sevenmachines ppa from "System >> Software Sources >> Other Software" then run FLASH-AID again. There is an icon in Firefox statusbar and nav toolbar, that allows to run it again.

What kind of error do you get on the BBC language site?

Hello lovinglinux, thx again for your rapid reaction. I have disabled the sevenmachines ppa and ran Flash-Aid again as indicated but to no avail.
As for the BBC series: Its seems to start all-right but 

-it's impossible to skip the intro (works well in W7)
-if I pick the 1st video a second screen opens where I have to indicate whether I'm male or female (voices are different). This is not possible (works well in W7, whereafter you get a start button to get the 1st video going).
-if I pick video series n°2 from the main screen, again it seems to start all right. It gives a (separate) text screen and there is a top progress bar that indicates "things" are loading. I then get the bottom start button but that does not function. There is also a full screen and a sound button, both of them do not work.
All of these work flawlessly in W7 using the same Firefox 3.6.8
Where do I go for now? Any other thouhts? 
FYI, I can play normal youtube videos without problems.

---

### Post by Alver on 2010-09-07
> **lovinglinux said:**
> There is nothing wrong with your report, except that you have a third-party ppa repository installed. Try to disable the sevenmachines ppa from "System >> Software Sources >> Other Software" then run FLASH-AID again. There is an icon in Firefox statusbar and nav toolbar, that allows to run it again.

What kind of error do you get on the BBC language site?

Hello lovinglinux, FYI I have added a print-screen of my effort to start n°2 video. It may give a better idea of what is going on. Hope it helps.

Thx

Alver

---

### Post by lovinglinux on 2010-09-07
> **Alver said:**
> Hello lovinglinux, thx again for your rapid reaction. I have disabled the sevenmachines ppa and ran Flash-Aid again as indicated but to no avail.
As for the BBC series: Its seems to start all-right but 

-it's impossible to skip the intro (works well in W7)
-if I pick the 1st video a second screen opens where I have to indicate whether I'm male or female (voices are different). This is not possible (works well in W7, whereafter you get a start button to get the 1st video going).
-if I pick video series n°2 from the main screen, again it seems to start all right. It gives a (separate) text screen and there is a top progress bar that indicates "things" are loading. I then get the bottom start button but that does not function. There is also a full screen and a sound button, both of them do not work.
All of these work flawlessly in W7 using the same Firefox 3.6.8
Where do I go for now? Any other thouhts? 
FYI, I can play normal youtube videos without problems.

See second item at [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Alver on 2010-09-08
> **lovinglinux said:**
> See second item at [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)
Hello lovinglinux, I applied the patch as indicated (adding a line in npviewer). That did the job! It is all WORKING now.

Thx for for your research work and help for my problem. I hope others will use this simple patch as well.

Alver

---

### Post by lovinglinux on 2010-09-08
> **Alver said:**
> Hello lovinglinux, I applied the patch as indicated (adding a line in npviewer). That did the job! It is all WORKING now.

Thx for for your research work and help for my problem. I hope others will use this simple patch as well.

Alver

You are welcome. Lots of people use this hack.

---

### Post by lovinglinux on 2010-09-16
FLASH-AID 1.0.12 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.12rc, but it is identical to the final version.

This version adds support for the new 64bit flash version.

---

### Post by oldos2er on 2010-09-16
> **lovinglinux said:**
> This version adds support for the new 64bit flash version.

Awesome. Thank you!

---

### Post by lovinglinux on 2010-09-16
> **oldos2er said:**
> Awesome. Thank you!

You are welcome.

---

### Post by SpetsnazC4 on 2010-09-16
Awesome job. Fixed my Flash problem. Flash was working fine and all of the sudden the playback became very jerky and choppy. Found your extension looking for flash removal instructions to do a reinstall. Ran your extension and everything works great again. Thanks.

---

### Post by lovinglinux on 2010-09-16
> **SpetsnazC4 said:**
> Awesome job. Fixed my Flash problem. Flash was working fine and all of the sudden the playback became very jerky and choppy. Found your extension looking for flash removal instructions to do a reinstall. Ran your extension and everything works great again. Thanks.

You are welcome.

:popcorn:

---

### Post by lovinglinux on 2010-09-18
FLASH-AID 1.0.13 was released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.13rc, but it is identical to the final version.

This version only removes the extension menu icon from the statusbar, due to upcoming changes in Firefox 4, in which the statusbar will be replaced by a new addons bar. So from now on, the extension will only be accessible from the navigation toolbar.

[IMG]http://tinyurl.com/28ok7q7[/IMG]

Users that prefer to access FLASH-AID from the bottom of the browser will be allowed to move it to the new addons bar in Firefox 4.

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)

---

### Post by mvandemar on 2010-09-24
> **lovinglinux said:**
> This version only removes the extension menu icon from the statusbar, due to upcoming changes in Firefox 4, in which the statusbar will be replaced by a new addons bar. So from now on, the extension will only be accessible from the navigation toolbar.

The addon updated for me today, and now it's not showing for me at all, in either location.

[img]http://www.endlesspoetry.com/images/flashaid-not-there.png[/img]

How do I activate it?

-Michael

---

### Post by lovinglinux on 2010-09-24
> **mvandemar said:**
> The addon updated for me today, and now it's not showing for me at all, in either location.

[img]http://www.endlesspoetry.com/images/flashaid-not-there.png[/img]

How do I activate it?

-Michael

Right-click in the toolbar and select customize, then drag the extension icon to the toolbar.

---

### Post by lovinglinux on 2010-09-28
FLASH-AID 1.0.14 was released today and is available for download through the "Other Downloads" section. It will be available in the Stable Channel as soon it gets reviewed by Mozilla editors. If you are using a beta version of FLASH-AID, please update to a stable version, since betas will no longer be provided.

This version updates flash 64bit to square preview 2.

---

### Post by learner4ever on 2010-10-16
thanks a lot! this is awesome..:)

---

### Post by lovinglinux on 2010-10-16
> **learner4ever said:**
> thanks a lot! this is awesome..:)

You are welcome.

---

### Post by lovinglinux on 2010-10-22
FLASH-AID 1.0.15 was released today and is available for download through the Other Downloads section. It will be available in the Stable Channel as soon it gets reviewed by Mozilla editors. 

This version fixes gnash removal in Maverick, due package name change.

---

### Post by static chaser on 2010-10-26
I cant seem to get Flash to work. I have 64 bit FF 4 installed in /opt. I downloaded it from the FF site. It is version 4.0b6. I have also tried Flash-Aid several time, both 64 bit and 32 bit. I have used Flash-Aid several times to resolve problems in the past and it worked great for me. I also tried installing Flash manually but no good.  I also have the ppa site activated for FF. I am using Meerkat. Any help would be appreciated.

---

### Post by lovinglinux on 2010-10-26
> **static chaser said:**
> I cant seem to get Flash to work. I have 64 bit FF 4 installed in /opt. I downloaded it from the FF site. It is version 4.0b6. I have also tried Flash-Aid several time, both 64 bit and 32 bit. I have used Flash-Aid several times to resolve problems in the past and it worked great for me. I also tried installing Flash manually but no good.  I also have the ppa site activated for FF. I am using Meerkat. Any help would be appreciated.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by static chaser on 2010-10-27
When I do the about:plugins Flash does not show up.  The FF version is:
Mozilla/5.0 (X11; Linux i686 on x86_64; rv2:0b6) Gecko/20100101 Firefox/4.0b6.

file:///home/day/Desktop/firefox-report.txt


Ubuntu Architecture

Linux Home 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox-3.0					deinstall
firefox-3.5					deinstall
firefox-4.0					deinstall

Firefox binaries

/usr/bin/firefox: ERROR: cannot open `/usr/bin/firefox' (No such file or directory)
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

jaunty-partner.list
jaunty-partner.list.distUpgrade
jaunty-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mozillateam-firefox-stable-karmic.list
mozillateam-firefox-stable-karmic.list.distUpgrade
mozillateam-firefox-stable-karmic.list.save
nilarimogard-webupd8-karmic.list
nilarimogard-webupd8-karmic.list.distUpgrade
nilarimogard-webupd8-karmic.list.save
silverwave-one-daily-a-month-0-lucid.list
silverwave-one-daily-a-month-0-lucid.list.distUpgrade
silverwave-one-daily-a-month-0-lucid.list.save
silverwave-one-daily-a-month-1-lucid.list
silverwave-one-daily-a-month-1-lucid.list.distUpgrade
silverwave-one-daily-a-month-1-lucid.list.save
suraia-ppa-karmic.list
suraia-ppa-karmic.list.distUpgrade
suraia-ppa-karmic.list.save
tualatrix-ppa-karmic.list
tualatrix-ppa-karmic.list.distUpgrade
tualatrix-ppa-karmic.list.save
ubuntu-mozilla-daily-ppa-lucid.list
ubuntu-mozilla-daily-ppa-lucid.list.distUpgrade
ubuntu-mozilla-daily-ppa-lucid.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntuone-beta-sources.list.distUpgrade
ubuntuone-beta-sources.list.save

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

---

### Post by lovinglinux on 2010-10-27
> **static chaser said:**
> When I do the about:plugins Flash does not show up.  The FF version is:
Mozilla/5.0 (X11; Linux i686 on x86_64; rv2:0b6) Gecko/20100101 Firefox/4.0b6.

file:///home/day/Desktop/firefox-report.txt


Ubuntu Architecture

Linux Home 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

You are using a 32bit browser on a 64bit system, so the browser won't be able to detect the plugin. Download Firefox 64bit. See [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

Additionally, when installing a Firefox manually, you need to create a symlink from /usr/lib/mozilla/plugins to your local Firefox plugin folder. See [http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html)

---

### Post by static chaser on 2010-10-27
I reloaded FF4 from the ppa and flash works good now. Thanks for the help. I use your customization & Flash-aid threads to fix problems.

---

### Post by lovinglinux on 2010-10-27
> **static chaser said:**
> I reloaded FF4 from the ppa and flash works good now. Thanks for the help. I use your customization & Flash-aid threads to fix problems.

You are welcome.

---

### Post by lovinglinux on 2010-11-03
FLASH-AID 1.0.16 was released today, has already been approved by Mozilla and is available for download. 

This version fixes a bug that affected only users with Firefox profile names containing spaces.

---

### Post by Bluesan on 2010-12-05
^,

According to the Adobe Labs, there was an update to Square - Preview 3, on 11/30. Are we expecting an update to the extension?

(No worries, just curious.)

[http://labs.adobe.com/](http://labs.adobe.com/)

Edit: Adding...

[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by lovinglinux on 2010-12-05
> **Bluesan said:**
> ^,

According to the Adobe Labs, there was an update to Square - Preview 3, on 11/30. Are we expecting an update to the extension?

(No worries, just curious.)

[http://labs.adobe.com/](http://labs.adobe.com/)

Edit: Adding...

[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

I'm sorry for the delay. I have been so busy this week with the development of a new web site for my extensions, that I totally missed the update. 

You can get the new updated version of the extension (1.0.17) at:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/) 

Thanks for the reminder.

---

### Post by Bluesan on 2010-12-05
> **lovinglinux said:**
> I'm sorry for the delay. I have been so busy this week with the development of a new web site for my extensions, that I totally missed the update. 

You can get the new updated version of the extension (1.0.17) at:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/) 

Thanks for the reminder.

You're welcome, and thanks for the update.

:)

---

### Post by lovinglinux on 2010-12-05
> **Bluesan said:**
> You're welcome, and thanks for the update.

:)

You are welcome.

---

### Post by Vaphell on 2010-12-06
i got one minor nitpick: it appears that 64bit libflashplayer.so in /usr/lib/mozilla/plugins after the upgrade is owned by the user not by root.
Yesterday i updated it manually from tar.gz (flash-aid 1.17 was not officially released on mozilla site yet) and was surprised when i forgot sudo and it didn't complain. Apparently 1.16 made me an owner during the previous update and i didn't have to escalate my privileges. I chowned the file to root:root but today i let 1.17 run and now i own the .so again.

---

### Post by lovinglinux on 2010-12-06
> **Vaphell said:**
> i got one minor nitpick: it appears that 64bit libflashplayer.so in /usr/lib/mozilla/plugins after the upgrade is owned by the user not by root.
Yesterday i updated it manually from tar.gz (flash-aid 1.17 was not officially released on mozilla site yet) and was surprised when i forgot sudo and it didn't complain. Apparently 1.16 made me an owner during the previous update and i didn't have to escalate my privileges. I chowned the file to root:root but today i let 1.17 run and now i own the .so again.

I will investigate this right now. Please give me a few minutes...

---

### Post by lovinglinux on 2010-12-06
> **Vaphell said:**
> i got one minor nitpick: it appears that 64bit libflashplayer.so in /usr/lib/mozilla/plugins after the upgrade is owned by the user not by root.
Yesterday i updated it manually from tar.gz (flash-aid 1.17 was not officially released on mozilla site yet) and was surprised when i forgot sudo and it didn't complain. Apparently 1.16 made me an owner during the previous update and i didn't have to escalate my privileges. I chowned the file to root:root but today i let 1.17 run and now i own the .so again.

I did some tests and once libflashplayer.so is moved to /usr/lib/mozilla/plugins, I have no access to it, unless I use sudo. However, browsing the directory and checking the permissions reveals that libflashplayer.so is indeed owned by me. I did some additional tests outside the extension environment and could conclude that the problem lies in the mv command. When I use sudo cp instead of sudo mv, the file ownership is not preserved as I would expect. But when I use sudo mv, the ownership is retained. As far as I know, that shouldn't happen.

I will release a new version to deal with this, but this seems really odd to me.

---

### Post by lovinglinux on 2010-12-06
[SIZE="6"][COLOR="Red"]**WARNING:**[/COLOR][/SIZE]

All 64bit users that use Flash-Aid to install the 64bit square preview should update to Flash-Aid 1.0.18 as soon as possible. After installing it and restarting Firefox, the extension will ask for a flash update, which you should agree. If that doesn't happen for some reason, you should reinstall flash from the extension menu. The reason for that is [a security issue]("http://ubuntuforums.org/showpost.php?p=10207966&postcount=85").

Thanks to Vaphell for spotting this bug.

---

### Post by figg on 2010-12-26
I'd just like to say a big thank you for creating this Flash Aid program. I was having lingering post-OS-installation issues for about a month after upgrading to Ubuntu 10.10 and this is a life-saver!

---

### Post by lovinglinux on 2010-12-26
> **figg said:**
> I'd just like to say a big thank you for creating this Flash Aid program. I was having lingering post-OS-installation issues for about a month after upgrading to Ubuntu 10.10 and this is a life-saver!

You are welcome.

:popcorn:

---

### Post by isuru_opt on 2010-12-30
Hi lovinglinux,

First of all a big thank for your effort to support others. 
I encounter a similar problem and hope you can help me.
I cannot view clips in youtube or metacafe, they all go in fast forward mode. Then I saw several people have recomended Flash-Aid and I installed it. I tried installing both 32 and 64 bit versions of flash. but unfortunately it didnot solve my problem. 

Below are my settings. 

uname -a
Linux isihome 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Firefox info
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13

I went through all the pages in forum post. I couldnot find one to resolvbe my isssue and hope you could help me.

I have latest version of Flash-Aid ( 1.0.18 )

regards,
Isuru

---

### Post by lovinglinux on 2010-12-30
> **isuru_opt said:**
> Hi lovinglinux,

First of all a big thank for your effort to support others. 
I encounter a similar problem and hope you can help me.
I cannot view clips in youtube or metacafe, they all go in fast forward mode. Then I saw several people have recomended Flash-Aid and I installed it. I tried installing both 32 and 64 bit versions of flash. but unfortunately it didnot solve my problem. 

Below are my settings. 

uname -a
Linux isihome 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Firefox info
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13

I went through all the pages in forum post. I couldnot find one to resolvbe my isssue and hope you could help me.

I have latest version of Flash-Aid ( 1.0.18 )

regards,
Isuru

Does it work using a clean Firefox profile?

BTw, this doesn't seem to be a Flash-Aid issue, so I would ask if you could post on the following thread instead: [http://ubuntuforums.org/showthread.php?t=1517564](http://ubuntuforums.org/showthread.php?t=1517564)

---

### Post by isuru_opt on 2010-12-30
Hi
Thanks for the quick reply. By clean firefox profile I hope you mean without Flash-Aid. Well It didnot work. I mean with or without Flash-Aid, I have videos running in fast forward mode. Thanks anyway. I will post it to the forum you suggested.

regards,
Isuru

---

### Post by pablo0151 on 2010-12-30
Just wanted to say a massive thanks for this add-on...some quality work.

---

### Post by lovinglinux on 2010-12-30
> **isuru_opt said:**
> Hi
Thanks for the quick reply. By clean firefox profile I hope you mean without Flash-Aid. Well It didnot work. I mean with or without Flash-Aid, I have videos running in fast forward mode. Thanks anyway. I will post it to the forum you suggested.

regards,
Isuru

It doesn't matter if it is with Flash-Aid or not, because the extension does not interact with browser after running the installer. What I meant was to test with a new profile, because sometimes Firefox settings, corrupted files, cookies and the cache can affect video display. So, starting with a clean profile would at least strike that possibility from the list.

> **pablo0151 said:**
> Just wanted to say a massive thanks for this add-on...some quality work.

Thanks a lot. BTW, you should see version 2.0, which is under development. I am really excited about it, since it has tons of new features, like option to select which plugins to remove and install, flash beta update checker, flash tweaks and more. In the easy mode (default), the extension detects various possibly conflicting plugins to be removed, available tweaks to be applied and the best plugin option for the system architecture,  thus providing an one-click installation solution.

Sneak peek:

[IMG]http://goo.gl/77s5s[/IMG]

---

### Post by mrnettles on 2010-12-31
That's fantastic, thanks. Worked perfectly. Now I can watch [this]("http://www.youtube.com/watch?v=v_kJ5m6Bsts") on my mum's computer too!

---

### Post by lovinglinux on 2011-01-01
I just released [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and I'm very excited about it, because it has tons of new features, including 64bit updates.

[IMG]http://goo.gl/77s5s[/IMG]

By default, the extension detects currently installed flash plugins in various locations, like /usr/lib/mozilla/plugins, ~/.mozilla/plugins, /opt/firefox/plugins and even the wine directory. It also detects gnash, swfdec, lightspark, adobe-flashplugin, flashplugin-nonfree and flashplugin-installer. When executed, it will remove all detected flash plugins and install the best option for the system, considering architecture and Ubuntu version. It will also apply some tweaks like OverrideGPUValidation, to improve performance and avoid fullscreen erros.

The default mode automatically select all those options and install the beta version from Adobe, except on Hardy 64bit, in which it installs the version from the repositories. The square preview 64bit crashes in fullscreen on Hardy. Anyway, the default mode is pretty simple and automatic. You just need to click a button. However, the extension also includes an "Expert Mode", which allows to select which plugin to install and remove. Among the options of plugins to install, there is a custom mode that allows to insert a local path to the tar.gz file downloaded from Adobe or the url from Adobe site and the extension takes care of extracting and installing it.

One of the best new features is that the extension is now capable of checking for updates of the beta versions and prompt if you want to run Flash-Aid to get the update. 

In Flash-Aid 1.0.x when Adobe released a new beta and removed the old link from the site, I had to update the extension in order to make it work again. This is no longer necessary, because the extension downloads from a redirection link on my site, that simply points to the download url on Adobe's site. So all I need to update the link and the update timestamp and the extension will warn you about the new version and get the proper file. 

I have tested it on Hardy 32/64bit, Karmic 32/64bit, Lucid 32/64bit, Maverick 32/64bit on Firefox 4.0b8, 4.0b9pre, 3.6.13 and 3.5.16. 

This version won't be displayed in the Mozilla site until they review it, but you can get from the extension web site:

[http://www.webgapps.org/addons/flash-aid]("http://www.webgapps.org/addons/flash-aid")

I haven't updated the documentation yet, but the extension also include some tips and should be pretty easy to understand how it works.

Have fun and Happy New Year.

---

### Post by Bluesan on 2011-01-02
^,

Info...

Just reinstalled Lucid, and when I tried to grab the new version from your site (link), I'm running into a page of this...

PK
&#65533;&#65533;&#65533;&#65533;&#65533;…Mž=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;chrome/UT	&#65533;‰pMiÜMux&#65533;è&#65533;&#65533;è&#65533;&#65533;PK
<snip>

How do I solve, or should I just wait for the extension to show up in Mozilla?

Thx

---

### Post by lovinglinux on 2011-01-02
> **Bluesan said:**
> ^,

Info...

Just reinstalled Lucid, and when I tried to grab the new version from your site (link), I'm running into a page of this...

PK
&#65533;&#65533;&#65533;&#65533;&#65533;…Mž=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;chrome/UT	&#65533;‰pMiÜMux&#65533;è&#65533;&#65533;è&#65533;&#65533;PK
<snip>

How do I solve, or should I just wait for the extension to show up in Mozilla?

Thx

Can you see the page with the download link? 

Try this:

[http://www.webgapps.org/downloads/addons-firefox](http://www.webgapps.org/downloads/addons-firefox)

or this:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)


Which browser you are using to download?

---

### Post by Bluesan on 2011-01-02
> **lovinglinux said:**
> Can you see the page with the download link? 

Try this:

[http://www.webgapps.org/downloads/addons-firefox](http://www.webgapps.org/downloads/addons-firefox)


I see your blog page fine, but, the link gives a page of this...

H¸¬tÎ*Ð¤
&&#352;U&#8226;&#8224;    S&#8221;É-Ù¸¿Äu6ÈrJNXQ&#402;L{Çõ¸&#339;~À&#8249;Æ®ë&#381;ó&#8250;gS&#352;§aqðüÎýÙèÈ6=!¿ð&«üÎg©&#8230;ÄÔ    ¦röaa¡=+TÔµT.,ÛìaC&#352;e»&#376;&#8226;¨s£Ði«ITL
(
Y¤H$T¹&#381; J{æ<Ë¦Ý&#402;&#8211;84*R¥¤l¯6ãöFqL¸NfÈRäd¤ömßîG]{Eë2EM^&#339;`è7w¡+nq\q&#8218;L*¸¾¿&#352;\KØW
m'÷&#382;¾ÅMiMº=_'òà(*ä&#8224;Yæ:UÞi~zd}1±&#8224;vºIþkþiÇ.És%ØÃp0ÀKN    *çç&#352;°ÿ¯!Ô
áû¹l&#8225;Û&#8212;C    ^p&#8364;&#376;PK&#65533;&#65533;&#65533;¹!>67òÆì&#65533;&#65533;`&#65533;&#65533; &#65533;&#65533;chrome/locale/en-US/flashaid.dtdUT    &#65533;¾*M/! Mux&#65533;è&#65533;&#65533;è&#65533;&#65533;ÍX]o·}¿¿&#8218;WON!K@Rô¡(.ÛÄI&#65533;'b%A©Ý&#8216;&#8211;5&#8212;Ü&#8217;\)êÃýí÷?Ö»²ì¸èKÃâÇp&#8224;&#339;9s8Ü_þýúÃúÝú7ñ²¶zg|Z&#8220;³Ø[g[á¨³^ëyq±ì½[jµYnµôM§û2&#8212;ª,ä&#8482;<!äÞ>&#8250;ýç_¿L¬|°æÊýUÆ&#353;-&#8211;=ÅÂJº`NNÑå±,I&#8211;¼Ùû&#381;ÿRE?·çÉJ¸&#8211;?þµ¡êösWË&#65533;&#8250;³Ø[ëDÔ/ú4ñÐ&#8218;µê°èkCFxÒTev"4$l&#8221;5"XQ×8bô-ñ,yPZ&#8249;Ú&#338;¶²RìÉ&#8230;o8ñ»ÇüVéì¬mv²ëüÂº°¦"H×ò¸ëFù$WY$â&#381;i}&#338;&#8224;&#8218;j    0h»ÑN`&#8218;M{!÷Ri¹)¢&#376;æâÐ¨ªØ&#8364;=ø&#8220;ÍâX5r*2$ÔVm/¹§(¦ùx¡h&#376;e&#8222;u5¢&#8249;U0BnlFV³K/÷>Øöó§kÄ$6ÅEB'z§¡Nh[I
Ü&#8222;fùW¶ê[Âá£÷g&#8220;î&#402;rkkuP&#732;}Q&#65533;&#376;¸bç\¾T5Â1Ö¿Ãàî&#8220;Lõ~°!g*&#8250;Æ&#8216;p,÷úU}@&#353;åÆ&#8482;¹aWE&#8211;}ë+§ºÀ&#382;tÔÚ}&#338;ôV«&#8222;»&#8221;~^æ0K<uá@òvêæ×ß:Dä½*ã^¸-¸3¹R&#381;¶öÛÊÙ&#710;*Yî&#8249;.d³&#65533;&#8211;æ(_üo¹hí&#376;&#8364;³\n&#8220;èò&#8225;&#8211;Yj*«ë&#8212;7o_¾{µ&#8218;9&#8221;&#8216;Lwî
&#376;[&#8230;Îõë&#8216;üXæá&#8220;ÏÒÏc$¶c    nÅFÚä)¼%0ðÿÉ¨ª)¥?·7ÇÓ:#@r<(òè&#8482;E¬ëÅó±+écÆUj&#65533;DÊ9±qÈMø\ºªQ<Û;ä£/&#382;o&#65533;d|b¥¸&#710;Ä&#8224;ó21Ò&#65533;t,Ä»&#8221;¾i"®
vÀ)jÝ?,Á&#352;ß&#8216;&#352;z]&#8216;Æ&#338;¨&#8364;ÁÛhc¢ÅGûéÇ¿q´&#376;~ü§íK"<ÐHnð&op&#8211;&#352;~&#8249;_«]<®¼[1µC©Ä¸{×;Eêû&#8221;w«&#339;&#8216;³ÜRt&#339;&#8250;çòC·Wt ·f¢³ÒMÄý&#353;Üï>n"&#353;&#338;µ¤m¬ëãj}·Ü[Eº¾ÛÉ7äÀyô;×úG\)Î!ÙÞ¬>&#8216;ZÕ&#8482;å&#8225;q    1&#353;¹P-HjW"pØ}+ãmÉØ±&#353;ÃÜk
F%DYyßÓÔ&#376;%...

<snip>

> or this:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
This link works fine. I've downloaded the new version, and installed it with no problems.


> Which browser you are using to download?Firefox 3.6.13

---

### Post by lovinglinux on 2011-01-02
> **Bluesan said:**
> I see your blog page fine, but, the link gives a page of this...

H¸¬tÎ*Ð¤
&&#65533;ŠU•†    S”É-Ù¸¿Äu6ÈrJNXQƒL{Çõ¸œ~À‹Æ®ëŽó›gSŠ§aqðüÎýÙèÈ6=!¿ð&«üÎg©…ÄÔ&#65533;    ¦röaa¡=+TÔµT.,ÛìaCŠe»Ÿ•¨s£Ði«ITL
...

Weird. I have no idea why this is happening. It works for me on Firefox, Opera and Chrome. I will make some some tests to try to figure out what's wrong.

> **Bluesan said:**
> This link works fine. I've downloaded the new version, and installed it with no problems.

Great. Let me know if you experience any problems with the extension.

---

### Post by Bluesan on 2011-01-02
> **lovinglinux said:**
> Weird. I have no idea why this is happening. It works for me on Firefox, Opera and Chrome. I will make some some tests to try to figure out what's wrong.

I'm using NoScript, but, I still get the same odd results whether I allow just the top domain (webgapps), or temporaily allow everything. Strange indeed.



> Great. Let me know if you experience any problems with the extension.I just read through all of the new info on using the extension. Easily followed, and understood (including expert mode). Well done. Thanks again.

---

### Post by bapoumba on 2011-01-02
FYI, the site loads okay for me, firefox 3.16.3 maverick.

---

### Post by Bluesan on 2011-01-02
Adding...

One small thing, that would be a plus. Please allow access to the extension dialog through the Add-ons preferences button (currently disabled). I, like many I would suppose, prefer to "talk" with an extension through the Add-on list, rather than having a lot of buttons on the navigation tool bar.

---

### Post by lovinglinux on 2011-01-02
> **Bluesan said:**
> I'm using NoScript, but, I still get the same odd results whether I allow just the top domain (webgapps), or temporaily allow everything. Strange indeed.

I just tested that address in more than 50 browser/OS combinations and they all worked. I guess the problem is in your FF profile. Can you test it with a different browser?

> **Bluesan said:**
> I just read through all of the new info on using the extension. Easily followed, and understood (including expert mode). Well done. Thanks again.

Nice. Thanks for the feedback.

---

### Post by lovinglinux on 2011-01-02
> **bapoumba said:**
> FYI, the site loads okay for me, firefox 3.16.3 maverick.

Thanks for the feedback.

> **Bluesan said:**
> Adding...

One small thing, that would be a plus. Please allow access to the extension dialog through the Add-ons preferences button (currently disabled). I, like many I would suppose, prefer to "talk" with an extension through the Add-on list, rather than having a lot of buttons on the navigation tool bar.

Done. It will be available in the next version.

---

### Post by Bluesan on 2011-01-02
> **lovinglinux said:**
> I just tested that address in more than 50 browser/OS combinations and they all worked. I guess the problem is in your FF profile. Can you test it with a different browser?


I can download the .zip file with Chromium, so, it must be with the FF profile. New install of Lucid this morning, as I mentioned in my first post, so, I'm not sure what to do, nor whether I'll even worry about it. Thanks for checking it out.

---

### Post by Bluesan on 2011-01-02
^,

I tried a new Firefox profile on the other Lucid install, and the problem persisted. Now, I'm typing this from an absolutely fresh, virgin install of Lucid, and the problem still exists. An interesting puzzle, but, I've got other things to do, so, I won't be able to revisit this for a while...

> PK
&#65533;&#65533;&#65533;&#65533;&#65533;&#8230;M&#382;=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;chrome/UT    &#65533;&#8240;pMiÜMux&#65533;è&#65533;&#65533;è&#65533;&#65533;PK
&#65533;&#65533;&#65533;&#65533;&#65533;M&#382;=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;chrome/locale/UT    &#65533;&#8218;pMlÜMux&#65533;è&#65533;&#65533;è&#65533;&#65533;PK
&#65533;&#65533;&#65533;&#65533;&#65533;Rd¶<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;chrome/locale/en-US/UT    &#65533;&#338;ù÷KoÜMux&#65533;è&#65533;&#65533;è&#65533;&#65533;PK&#65533;&#65533;&#65533;<!>Ç?U&#65533;&#65533;Ë&#65533;&#65533;&&#65533;&#65533;chrome/locale/en-US/strings.propertiesUT    &#65533;C¦M/! Mux&#65533;è&#65533;&#65533;è&#65533;&#65533;Õ&#8220;ßj&#402;0Æï}&#352;SØ&ìdÈj©Ðµe
c°&#8250;S=Ö°&#732;H&#338;µÝÓ/Q·²í¢7öÏr£9G¾óåó&#8212;T
òn&#8225;[o¢{NÂyM&#402;ñ^e...

---

### Post by lovinglinux on 2011-01-02
> **Bluesan said:**
> ^,

I tried a new Firefox profile on the other Lucid install, and the problem persisted. Now, I'm typing this from an absolutely fresh, virgin install of Lucid, and the problem still exists. An interesting puzzle, but, I've got other things to do, so, I won't be able to revisit this for a while...

The problem is that I had configured the download in a way that the file would be opened by Firefox and the installation would start automatically, instead of downloading the file to a folder.

For some reason Firefox was opening the xpi file as if it was a html page instead of interpreting it as an extension file.

Problem fixed. Thanks.

---

### Post by Bluesan on 2011-01-03
> **lovinglinux said:**
> The problem is that I had configured the download in a way that the file would be opened by Firefox and the installation would start automatically, instead of downloading the file to a folder.

For some reason Firefox was opening the xpi file as if it was a html page instead of interpreting it as an extension file.

**Problem fixed**. Thanks.

Glad you got it worked out.

---

### Post by Bluesan on 2011-01-05
> **Bluesan said:**
> Adding...

One small thing, that would be a plus. **Please allow access to the extension dialog through the Add-ons preferences button (currently disabled)**. I, like many I would suppose, prefer to "talk" with an extension through the Add-on list, rather than having a lot of buttons on the navigation tool bar.

Just got the 2.0.1 upgrade, thanks for adding...

---

### Post by lovinglinux on 2011-01-06
> **Bluesan said:**
> Just got the 2.0.1 upgrade, thanks for adding...

Oops, I forgot to put that in the changelog and to announce here. :oops:

This version was released mainly to deal Swiftfox issues on 64bit. Since they do not release 64bit versions of the browser, it can't load the plugins. Now there is a new rule that deals with that, by installing two versions of flash. The system folder gets the 64bit version and the ~/.mozilla/plugins/ gets the 32bit version, only when the browser is 32bit and the OS 64bit.

---

### Post by lovinglinux on 2011-01-07
Released version 2.0.2, which adds an option to use Google Chrome plugin on 32bit systems and a couple of minor bug fixes.

---

### Post by TBABill on 2011-01-21
Lovinglinux, I just installed 2.0.2 on a fresh 10.04 Xubuntu install and it is not working. It opens a terminal, but the terminal window doesn't actually do anything. It doesn't even open to show ```
bill@bill-laptop:~$
``` Any ideas what the hangup in the script it executes could be, or what error I could have made? I use Flash Aid on all Ubuntu or Mint installs but this time something borked.

---

### Post by TBABill on 2011-01-21
Disregard - the path to the terminal is different in Xubuntu and has to be changed manually to /usr/bin/xfce4-terminal. I changed the path and it worked fine. Perhaps an indicator somewhere to notify the end user of this requirement on Xubuntu would be of great assistance, and another for Kubuntu if it is different again in that DE?

---

### Post by lovinglinux on 2011-01-22
> **TBABill said:**
> Disregard - the path to the terminal is different in Xubuntu and has to be changed manually to /usr/bin/xfce4-terminal. I changed the path and it worked fine.

By default, the extension uses /usr/bin/x-terminal-emulator, however it tries to detect gnome-terminal and konsole. If the extension finds one of those, it changes the path automatically, the first time you run the extension. 

I will add /usr/bin/xfce4-terminal to the list in the next version.

> **TBABill said:**
> Perhaps an indicator somewhere to notify the end user of this requirement on Xubuntu would be of great assistance, and another for Kubuntu if it is different again in that DE?

If the extension cannot find the terminal emulator, it displays a warning instead of the script. Additionally, there are instructions below the path field explaining what to do. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181727&stc=1&d=1295703160[/IMG]

---

### Post by static chaser on 2011-02-07
I have a similar problem as TRABill. I get an error that says "There was an error creating child process for this terminal". It may be because I have reloaded 9.10 on my computer but this time I created a separate partition for home. My terminal window opens but it is blank when this happens. I really like Flash-Aid because it is so easy to solve Flash problems. Any help would be appreciated.

---

### Post by WinRiddance on 2011-02-08
BUMMER ... I thought Flash Aid would be a solution for me too, but it wasn't.

I've been having flash problems ever since Ubuntu 10.04 ... actually since version 9.04 but the problems only got really bad since 10.04 which was horrible, and now 10.10 where I can cause crashes on flash pages at will. [This page]("http://www.steinfein.org/") for example, has our [YouTube browse feature with assorted video clips.]("http://www.steinfein.org/") If I'm lucky I make it all the way to a second clip, but I never make it past the third clip before my system crashes completely.

I'm not a gamer and I don't use any other OS, just Ubuntu in its own partition. All along I've been suspecting the ATI proprietary drivers from my 64bit dual core laptop but half the people I've spoken to in forums keep insisting that the crashes are flash related. Well, today I installed flash aid which did indeed find something to replace and to tweak. I didn't use the expert settings, just ran the test, and then did the install.

GOOD NEWS: My cpu didn't even start screaming when I started viewing videos on above site.

BAD NEWS:  Never made it past the third clip before the system crashed ... hard reset required.

Granted, my FF pages do seem to load a lot faster now, enabling me to crash my system even faster (kidding) ... so I'm thinking of switching to openSUSE next since that's supposed to be one of the most rock solid desktop linux versions there is. Stability really means a lot to me and I've been fighting this flash situation forever now (or so it seems) ....

---

### Post by beew on 2011-02-09
> **WinRiddance said:**
> BUMMER ... I thought Flash Aid would be a solution for me too, but it wasn't.

I've been having flash problems ever since Ubuntu 10.04 ... actually since version 9.04 but the problems only got really bad since 10.04 which was horrible, and now 10.10 where I can cause crashes on flash pages at will. [This page]("http://www.steinfein.org/") for example, has our [YouTube browse feature with assorted video clips.]("http://www.steinfein.org/") If I'm lucky I make it all the way to a second clip, but I never make it past the third clip before my system crashes completely.

I'm not a gamer and I don't use any other OS, just Ubuntu in its own partition. All along I've been suspecting the ATI proprietary drivers from my 64bit dual core laptop but half the people I've spoken to in forums keep insisting that the crashes are flash related. Well, today I installed flash aid which did indeed find something to replace and to tweak. I didn't use the expert settings, just ran the test, and then did the install.

GOOD NEWS: My cpu didn't even start screaming when I started viewing videos on above site.

BAD NEWS:  Never made it past the third clip before the system crashed ... hard reset required.

Granted, my FF pages do seem to load a lot faster now, enabling me to crash my system even faster (kidding) ... so I'm thinking of switching to openSUSE next since that's supposed to be one of the most rock solid desktop linux versions there is. Stability really means a lot to me and I've been fighting this flash situation forever now (or so it seems) ....

Maybe you should try  Lovinglinux's flashvideoreplacer plugin for firefox, it works for youtube and a few other sites as well. The idea is not to use flash at all. It is quite wonderful. I think it should work for 64 bit as well as long as mplayer does, though I have never use 64 bit.
[URL="http://ubuntuforums.org/showthread.php?t=1487327"]http://ubuntuforums.org/showthread.php?t=1487327
[/URL]

For watching youtube minitube is also great and it appears to use even less cpu apparently because it doesn't even need to work through firefox, which itself utilizes quite a bit of resources on older machines. Make sure you get the latest version (1.4) from a ppa instead of the outdated version in the Ubuntu repo. This one works nicely
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

Again I am not sure if it works for 64 bits.

---

### Post by beew on 2011-02-09
Hi, lovinglinux

I read that the latest flash version (10.2)works with vdpau. I have installed flash through flashaid and it doesn't seem to be using vdpau at all even after I have disabled compiz. I think flashaid did install the latest version even though I don't find any installed flash plugin in Synaptic. Am I missing something?

Thanks in advance for your advice.

---

### Post by lovinglinux on 2011-02-10
> **static chaser said:**
> I have a similar problem as TRABill. I get an error that says "There was an error creating child process for this terminal". It may be because I have reloaded 9.10 on my computer but this time I created a separate partition for home. My terminal window opens but it is blank when this happens. I really like Flash-Aid because it is so easy to solve Flash problems. Any help would be appreciated.

Change the path to the terminal emulator in the extensions preferences. If that doesn't solve the problem, then click the "Refresh" button, copy the content of the "Script Preview" tab, paste it on a new file, set the file to be executable and drag it to a terminal.

I will add an option to export the script to a file in the next version.

> **beew said:**
> Hi, lovinglinux

I read that the latest flash version (10.2)works with vdpau. I have installed flash through flashaid and it doesn't seem to be using vdpau at all even after I have disabled compiz. I think flashaid did install the latest version even though I don't find any installed flash plugin in Synaptic. Am I missing something?

Thanks in advance for your advice.

If you are using the default settings, then you won't see flash in Synaptic. The extension downloads the plugin from Adobe and extract it to the plugin folder.

You can check the version via Firefox Add-ons Manager.

---

### Post by marve12le on 2011-02-10
Released version 2.0.2, which adds an option to use Google Chrome plugin on 32bit systems and a couple of minor bug fixes.

---

### Post by onemanclapping on 2011-02-10
Quick question: After running the scrip in this plugin, am I suppose to get vdpau acceleration in my ION? I ran it and I still got no HW acceleration on youtube, with the nv drivers, compiz on and off.

Thanks in advance.

---

### Post by static chaser on 2011-02-11
Lovinglinux; If I start the terminal from Applications, then cut-and-paste the script into it, everything works fine. When I try to use the Execute button the terminal opens but the screen is blank and thats when I get the warning. My Gnome-terminal is in the bin/usr directory so I can't figure out what is going wrong. However, using the cut-and-paste works fine for me. Thanks for the help again.

---

### Post by onemanclapping on 2011-02-11
Problem solved!

Maybe it would be a good idea for Flash-aid to include this:

```
Open (or create) /etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1
```

As I had to do this with the new version of Flash in order to have vdpau acceleration.

---

### Post by beew on 2011-02-12
> **onemanclapping said:**
> Problem solved!

Maybe it would be a good idea for Flash-aid to include this:

```
Open (or create) /etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1
```

As I had to do this with the new version of Flash in order to have vdpau acceleration.


Thanks a lot for the tip man, now it works perfectly, tested on firefox and Opera. How would I figure that out without the Ubuntu forum? :)

Hope there will be better flash support for Linux overall in the future, not just for those who have the right Nvidia cards. :)

---

### Post by lovinglinux on 2011-02-12
> **onemanclapping said:**
> Problem solved!

Maybe it would be a good idea for Flash-aid to include this:

```
Open (or create) /etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1
```

As I had to do this with the new version of Flash in order to have vdpau acceleration.

Thanks. I will include in the next version.

---

### Post by lovinglinux on 2011-02-14
Flash-Aid 2.0.3 was released today and is available for download.

Changelog

- added xfce4-terminal detection
- fixed downloaded plugin tar package deletion
- added cache bypass to update check
- added vdpau hardware acceleration tweak
- added script export button
- umask issue fix

---

### Post by lovinglinux on 2011-02-14
> **static chaser said:**
> Lovinglinux; If I start the terminal from Applications, then cut-and-paste the script into it, everything works fine. When I try to use the Execute button the terminal opens but the screen is blank and thats when I get the warning. My Gnome-terminal is in the bin/usr directory so I can't figure out what is going wrong. However, using the cut-and-paste works fine for me. Thanks for the help again.

I have released version 2.0.3, which has an export button. So you just need to click it to export the script to your desktop, then drag it to a terminal. It does not fix your problem, but provides a convenient workaround.

---

### Post by jfd3220 on 2011-02-21
I had trouble viewing 720p flash videos last week so I installed flash-aid and it fixed the issue.  Today, however, even 480p is choppy, and I have no idea what happened.  I have run flash-aid several times today.  It keeps downloading the same file every time, flashplayer10_2_p3_64bit_linux_111710.tar.gz, and it completes without errors.  I have this version installed now: 10.3 d162.

EDIT: I tried switching to expert mode and using the Adobe 32-bit version instead of the default 64-bit beta, so now I have 10.2 r152 installed but the problem persists.

EDIT: This is strange.  Rebooting seems to have fixed the issue. Now I can view 720p fullscreen again.  Why would rebooting fix it when restarting firefox would not?

---

### Post by findelmundo on 2011-02-22
I ran Flash-aid, and was really hopeful, but it didn't fix my problem: watching youtube in fullscreen... Any suggestions anyone?

32bit Fujitsu Siemens Amilo Pro V2010, 2gbram, 13"

EDIT: I tried rebooting, but it didn't fix the problem. Still white(ish) screen instead of video in fullscreen...

---

### Post by jfd3220 on 2011-02-22
> **findelmundo said:**
> I ran Flash-aid, and was really hopeful, but it didn't fix my problem: watching youtube in fullscreen... Any suggestions anyone?

32bit Fujitsu Siemens Amilo Pro V2010, 2gbram, 13"

EDIT: I tried rebooting, but it didn't fix the problem. Still white(ish) screen instead of video in fullscreen...

I'm no expert but your machine might not have the power for fullscreen flash video.  I have an old Sony Vaio with similar specs and can't watch video with that either.  Here are the specs of yours: [http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_AMILO_Pro_V2010_Edition__6101108](http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_AMILO_Pro_V2010_Edition__6101108).

---

### Post by findelmundo on 2011-02-24
> **jfd3220 said:**
> I'm no expert but your machine might not have the power for fullscreen flash video.  I have an old Sony Vaio with similar specs and can't watch video with that either.  Here are the specs of yours: [http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_AMILO_Pro_V2010_Edition__6101108](http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_AMILO_Pro_V2010_Edition__6101108).

I have a dual boot with XP, and fullscreen works fine there, so I don't think its only a power issue...

---

### Post by lovinglinux on 2011-02-25
> **findelmundo said:**
> I have a dual boot with XP, and fullscreen works fine there, so I don't think its only a power issue...

Is not the same thing. You can't compare with Windows, because Flash uses to much CPU on Linux, due to it's inability to output via XV.

There are some things you could try tho.

See my tutorial [http://www.webgapps.org/flash/optimization](http://www.webgapps.org/flash/optimization)

Today I was trying to setup my laptop to watch a video streaming service similar to NetFlix, that uses flash. The laptop processing power is very weak and even with the tricks from my tutorial and using the latest flash, I wasn't able to get a perfectly smooth output and the video eventually froze after a while. So what I did was to change my nVidia settings to "Performance" and now it plays almost perfectly. So you could try to teak your video card driver settings.

---

### Post by beew on 2011-02-25
> **lovinglinux said:**
> 
Today I was trying to setup my laptop to watch a video streaming service similar to NetFlix, that uses flash. The laptop processing power is very weak and even with the tricks from my tutorial and using the latest flash, I wasn't able to get a perfectly smooth output and the video eventually froze after a while. So what I did was to change my nVidia settings to "Performance" and now it plays almost perfectly. So you could try to teak your video card driver settings.


Maybe your flashvideoreplacer is the way to go. :)

---

### Post by lovinglinux on 2011-02-27
> **beew said:**
> Maybe your flashvideoreplacer is the way to go. :)

I wish. But I probably won't be able to replace it, since the site uses rtsp. :-)

---

### Post by lovinglinux on 2011-03-09
Flash-Aid 2.0.4 was released today and is available for download.

Changelog

- switched to asynchronous XMLHttpRequest
- added beta security warning 
- delete temp folder on load to avoid Adobe latest beta left-overs

---

### Post by Kir_B on 2011-03-12
Hello Lovinglinux

I've been using your awesome Flashaid add-on for Firefox for quite some time now and have very recently started to experience my monitor crashing whenever I try to view videos on the Youtube site. Unfortunately, only a hard reboot will allow me to use my machine again, as the monitor will tell me that it doesn't have a signal.

After doing a little searching, I've come upon a few recommended fixes from the [Webupd8]("http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html") site (apparently, I'm not the only one having issues with Youtube). 

The fix that is going to (perhaps) work for me (#4), involves installing an older version of the flashplugin-installer.

```
wget http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
sudo dpkg -i flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```They also suggests that I lock the installer via the synaptic package manager, but the problem being, that synaptic doesn't appear to have it installed.???

Got any suggestions? Are you planning a temporary fix for this in Flashaid? If so, I may just wait.

I'm just curious, as I may just apply the fix and just watch my updates. (Where I live, I experience power outages due to snowy weather and have had my automatic updates disabled for the season, so it's not that big of a deal for me.)

Thanks again Lovinglinux.
Kirby ):P

---

### Post by lovinglinux on 2011-03-12
> **Kir_B said:**
> Hello Lovinglinux

I've been using your awesome Flashaid add-on for Firefox for quite some time now and have very recently started to experience my monitor crashing whenever I try to view videos on the Youtube site. Unfortunately, only a hard reboot will allow me to use my machine again, as the monitor will tell me that it doesn't have a signal.

After doing a little searching, I've come upon a few recommended fixes from the [Webupd8]("http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html") site (apparently, I'm not the only one having issues with Youtube). 

The fix that is going to (perhaps) work for me (#4), involves installing an older version of the flashplugin-installer.

```
wget http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
sudo dpkg -i flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```They also suggests that I lock the installer via the synaptic package manager, but the problem being, that synaptic doesn't appear to have it installed.???

Got any suggestions? Are you planning a temporary fix for this in Flashaid? If so, I may just wait.

I'm just curious, as I may just apply the fix and just watch my updates. (Where I live, I experience power outages due to snowy weather and have had my automatic updates disabled for the season, so it's not that big of a deal for me.)

Thanks again Lovinglinux.
Kirby ):P

This works for 32bit:

First of all, install Flash-Aid 2.0.5 from the extension web site, since this version fixes a problem related to the method explained below, among other things. I am experiencing issues while trying to upload to Mozilla, so version 2.0.5 is only available from the extension web site for now.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

Then download flash 10.1.85 archive from [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.1.85.3_and_9.0.283_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.1.85.3_and_9.0.283_archive.zip)

Extract the zip file, but not the packages inside it. Start Flash-Aid, then select the "Expert Mode" at the bottom of the extension dialog, then go to the "Installation Options tab", then select "Custom" in the "Version and Source" menu. Then click the "Search" button that will be displayed below the menu and browse the extracted file **flashplayer10_1r85_3_linux.tar.gz**, which is inside **Flash Player 10.1.85.3** >> **10_1r85_3**. Click the "Execute" button in the "Script Preview" tab. The extension will remove all flash versions and install the one from that file. Keep in mind this only works for 32bit. If you have 64 bit, you will need to find a 64bit tar.gz package somewhere or install the version from the repositories and replace the libflashplayer.so manually.

Also keep in mind is probably a security risk to use such an old version, since they discover critical vulnerabilities all the time in flash.

BTW, Synaptic will probably fail to install that version, because the package flashplugin-installer is just a downloader, that retrieves the plugin from Adobe, like Flash-Aid does. So it is very likely that the link to that version is no longer available from Adobe.

---

### Post by lovinglinux on 2011-03-13
You could also get rid of flash on YouTube using my extension FlashVideoReplacer.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

Make sure to get version 2.1.0, which is the most recent and full of new features.

---

### Post by Kir_B on 2011-03-14
Hello Lovinglinux.

Thank you so much for the oh so thorough response.

Unfortunately, I installed my brand new graphics card right after I posted, and long story short, it didn't work, and now, neither does my brand new computer! ](*,) 

Good thing I hadn't donated my old machine yet and it can serve me as a backup. :(

I won't be upgrading the flash on this one, so I won't be needing to use your fantastic instructions, but they may just help someone else.

Thanks again.
Kirby

---

### Post by lovinglinux on 2011-03-15
> **Kir_B said:**
> Hello Lovinglinux.

Thank you so much for the oh so thorough response.

Unfortunately, I installed my brand new graphics card right after I posted, and long story short, it didn't work, and now, neither does my brand new computer! ](*,) 

Good thing I hadn't donated my old machine yet and it can serve me as a backup. :(

I won't be upgrading the flash on this one, so I won't be needing to use your fantastic instructions, but they may just help someone else.

Thanks again.
Kirby

You are welcome.

Sorry to hear about your troubles with the graphics card.

---

### Post by kickwin on 2011-04-04
I installed Flash-Aid from Mozilla website. When I click on the new toolbar item, the flash-aid window opens but when I click Test, nothing happens. When I click on Execute,it just shows me the full code and all buttons disappear. I run Xubuntu 9.10. Please help me on this. Let me know if you need more details.

---

### Post by lovinglinux on 2011-04-04
> **kickwin said:**
> I installed Flash-Aid from Mozilla website. When I click on the new toolbar item, the flash-aid window opens but when I click Test, nothing happens. When I click on Execute,it just shows me the full code and all buttons disappear. I run Xubuntu 9.10. Please help me on this. Let me know if you need more details.

In this case, click "Export". It will save the script in your desktop. Drag the script file to a terminal and it will start the installation process.

---

### Post by kickwin on 2011-04-10
Thanks that worked. Do I need to always have flash-aid addon installed and or I can perhaps install/reinstall once a month and check for updates? I don't want another addon installed if it is not necessary.

---

### Post by lovinglinux on 2011-04-10
> **kickwin said:**
> Thanks that worked. Do I need to always have flash-aid addon installed and or I can perhaps install/reinstall once a month and check for updates? I don't want another addon installed if it is not necessary.

You don't need to have it installed. However, the extension checks for flash updates once a day. Whenever Adobe releases a new beta version, I update the extension check file and it warns you about the new version.

If you still don't want the extension to be loaded, simply disable it in the Add-ons Manager. It has the same effect as if you had uninstalled it. Nothing from that extension will be loaded when Firefox starts. It is easier than uninstalling and then reinstalling when you want.

I have several disable extensions.

---

### Post by laffinalltheway on 2011-04-30
Loving Linux, thank you for creating this add-on.  I had a hard time getting it to work until I used the export option.  That did the trick and now flash is working for me (finally).  Thanks again!

---

### Post by lovinglinux on 2011-04-30
> **laffinalltheway said:**
> Loving Linux, thank you for creating this add-on.  I had a hard time getting it to work until I used the export option.  That did the trick and now flash is working for me (finally).  Thanks again!

You are welcome. The export function was included to solve the problem that some users experience with the child process error. Also, if you manually start a terminal and leave it open before executing the script, it works.

Did you send me an e-mail as maryp...@...?

---

### Post by aeronutt on 2011-04-30
I was having white blocks and stuttery flash in Firefox 4, Natty. Flash-aid FIXED my problems. Thanks lovinglinux!!

---

### Post by lovinglinux on 2011-04-30
> **aeronutt said:**
> I was having white blocks and stuttery flash in Firefox 4, Natty. Flash-aid FIXED my problems. Thanks lovinglinux!!

You are welcome.

---

### Post by lovinglinux on 2011-05-15
Flash-Aid 2.1.0 was released today and is available for download.

This version brings several interface improvements, like a new wizard and quick installation modes.

**Changelog**

[LIST]
[*]added wizard and quick installation modes
[*]added several interface improvements
[*]moved some features to the toolbar menu
[*]moved preferences options to preference page
[*]removed script refresh (no longer needed)
[*]added dependency check
[*]added first install alert
[/LIST]

---

### Post by lovinglinux on 2011-05-22
Just wanted to share that tomorrow is Flash-Aid's one year birthday :-)

Thanks everyone for all the support.

Don't forget to grab version [2.1.1]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"), which has tons of improvements!

---

### Post by cong06 on 2011-05-26
Just a suggestion, I don't like having to use plugin buttons, I like to:
> Tools, -> Addons -> {addon name} -> Preferences

I found the change of configuration options to the button menu unintuitive.
I guess "unintuitive" isn't the right word, but it took me a while since I didn't know where to look.

Or maybe you can put buttons in the preferences that do the same thing?

---

### Post by lovinglinux on 2011-05-26
> **cong06 said:**
> Just a suggestion, I don't like having to use plugin buttons, I like to:
> Tools, -> Addons -> {addon name} -> Preferences

I found the change of configuration options to the button menu unintuitive.
I guess "unintuitive" isn't the right word, but it took me a while since I didn't know where to look.

Or maybe you can put buttons in the preferences that do the same thing?

Hi, thanks for your suggestions.

Which version are you using?

---

### Post by jaacko on 2011-05-28
Flash-Aid is simply awesome. Poor flash performance was my only problem with Ubuntu and now that's fixed. Thanks alot and keep up the great work!

Also I can't stop wondering why Adobe won't (I say 'won't' because I'm sure Adobe could) make flash work well on linux...

---

### Post by cong06 on 2011-05-28
> **lovinglinux said:**
> hi, thanks for your suggestions.

Which version are you using?

2.1.1

---

### Post by lovinglinux on 2011-05-28
> **jaacko said:**
> Flash-Aid is simply awesome. Poor flash performance was my only problem with Ubuntu and now that's fixed. Thanks alot and keep up the great work!

You are welcome.

> **jaacko said:**
> Also I can't stop wondering why Adobe won't (I say 'won't' because I'm sure Adobe could) make flash work well on linux...

I wonder when we will be able to completely replace flash with html5 :-)

> **cong06 said:**
> 2.1.1

Didn't you get a warning saying that you needed to run the Wizard from the toolbar menu? Wasn't the toolbar menu automatically placed on your toolbar?

---

### Post by cong06 on 2011-05-28
> **lovinglinux said:**
> 
Didn't you get a warning saying that you needed to run the Wizard from the toolbar menu? Wasn't the toolbar menu automatically placed on your toolbar?

Well, no. Not that I remember. I think I used it once at 2.1.0, and it had the normal options (in preferences) like I expected. Then I disabled it. I wanted to run it again (flash issues, among other things) so I re-enabled the now 2.1.1 version, and it had the new system.

Anyway, I still think it's unintuitive, but I appreciate the work you did enough to not pester you so much about it.
It was simply a suggestion.

---

### Post by lovinglinux on 2011-05-28
> **cong06 said:**
> Well, no. Not that I remember. I think I used it once at 2.1.0, and it had the normal options (in preferences) like I expected. Then I disabled it. I wanted to run it again (flash issues, among other things) so I re-enabled the now 2.1.1 version, and it had the new system.

Anyway, I still think it's unintuitive, but I appreciate the work you did enough to not pester you so much about it.
It was simply a suggestion.

Now I understand. You liked the dialog that was accessed via preferences, with everything in the same place. I thought that was confusing. Some users didn't know they had to run the script to install flash. So I have separated the script generation tools from the extension preferences and created the Wizard Mode. It wouldn't be possible to put all new options in the prefs. 

You didn't get the warning because it wasn't the first time you install it. It only warns new users. The add-on icon should have been added automatically. I suppose the problem was due to the upgrade.

For new users is pretty simple. When you start the browser for the first time after installation, the extension triggers an alert explaining what the user needs to do and where to find the menu, which is automatically placed on the Navigation Toolbar. Then the user just need to click the menu, select Wizard Mode and follow the instructions on screen.

---

### Post by Sirellyn on 2011-05-29
I'm using Natty 11.04 (64 bit), and firefox 4.0.1

Even with Flash-Aid, I can't get some sites to work.  In particular the game sites.  For example this one will ask me to upgrade flash:

[http://www.mochigames.com/game/hack-slash-crawl/](http://www.mochigames.com/game/hack-slash-crawl/)

But youtube will not.

I've used flash aid twice to completely uninstall and reinstall flash (wizard mode) and no go.  Any tips?

---

### Post by lovinglinux on 2011-05-29
> **Sirellyn said:**
> I'm using Natty 11.04 (64 bit), and firefox 4.0.1

Even with Flash-Aid, I can't get some sites to work.  In particular the game sites.  For example this one will ask me to upgrade flash:

[http://www.mochigames.com/game/hack-slash-crawl/](http://www.mochigames.com/game/hack-slash-crawl/)

But youtube will not.

I've used flash aid twice to completely uninstall and reinstall flash (wizard mode) and no go.  Any tips?

Click Flash-Aid icon, select *Help*, then *Generate Report*. Attach the file *firefox-report.txt* that will be created on your desktop, so I can have a better idea about your system.

---

### Post by Sirellyn on 2011-05-29
Ok I'll attach the report file to this message.  Thanks again for all your hard work on this.

---

### Post by Yellow Pasque on 2011-05-29
@Sirellyn: it looks like you have two Flash plugins installed. Try to figure out how that happened and see if you can undo it.

---

### Post by lovinglinux on 2011-05-29
> **Sirellyn said:**
> Ok I'll attach the report file to this message.  Thanks again for all your hard work on this.

This is weird. Indeed you still have two plugins.

Please go through the wizard again, but instead of executing the script at the end, export it then paste the content of the script so I can take a look at it.

---

### Post by Sirellyn on 2011-05-29
Ok here's the exported script.

---

### Post by lovinglinux on 2011-05-29
Try this:

```
sudo apt-get purge flashplugin-installer
```

Then post the output of:
```

file /usr/lib/mozilla/plugins/flashplugin-alternative.so
file /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
cat /home/markb/.mozilla/firefox/s2tnvv97.default/pluginreg.dat
```

---

### Post by 13east on 2011-05-29
[http://ubuntuforums.org/showthread.php?p=10878801#post10878801](http://ubuntuforums.org/showthread.php?p=10878801#post10878801)

> **lovinglinux said:**
> Disable the sevenmachines ppa and remove the flashplugin installed by it before running Flash-Aid.

-disabled sevenmachines ppa and removed the plugin installed by it
-ran flash-aid and installed flashplayer64 thorough the script

-still seeing issues w/ fullscreen video playback like needing to manually minimize firefox window to view fullscreen video, refusing to go to fullscreen and not covering the taskbar when going to fullscreen; not seeing the black screen which crashes the desktop environment as of yet.  Are these issues just a prevalent bug that are yet to be resolved or is there anything else I can do on my machine to fix it?

-also, will the flash plugin update normally through kubuntu update manager or do I need the flash-aid plugin installed to receive flash upgrades?

Any help you could provide with this issue would be very much appreciated.
Thank you.

---

### Post by Sirellyn on 2011-05-29
Here's the output:

```

markb@mouqol:~$ file /usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
markb@mouqol:~$ file /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so' (No such file or directory)
markb@mouqol:~$ file /var/lib/flashplugin-install/npwrapper.libflashplayer.so
/var/lib/flashplugin-install/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-install/npwrapper.libflashplayer.so' (No such file or directory)
markb@mouqol:~$ cat /home/markb/.mozilla/firefox/s2tnvv97.default/pluginreg.dat
Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1301673552000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1289952613000:1:1:$
Shockwave Flash 10.3 d162:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]
markb@mouqol:~$ 


```

---

### Post by lovinglinux on 2011-05-29
> **13east said:**
> -also, will the flash plugin update normally through kubuntu update manager or do I need the flash-aid plugin installed to receive flash upgrades?

If you installed the version from Adobe Labs, which is selected by default in the Wizard, then you need to keep Flash-Aid installed to receive update alerts. Once you receive an update alert, run the Wizard again to install the update.

> **13east said:**
> -still seeing issues w/ fullscreen video playback like needing to manually minimize firefox window to view fullscreen video, refusing to go to fullscreen and not covering the taskbar when going to fullscreen; not seeing the black screen which crashes the desktop environment as of yet.  Are these issues just a prevalent bug that are yet to be resolved or is there anything else I can do on my machine to fix it?

Any help you could provide with this issue would be very much appreciated.
Thank you.

You could try to disable hardware acceleration. Right-click on a Youtube video and select "Settings".

---

### Post by lovinglinux on 2011-05-29
> **Sirellyn said:**
> Here's the output:

Your Output is fine. You have the latest 64bit version from Adobe Labs.

Is the flash game you linked playing now?

---

### Post by Sirellyn on 2011-05-29
ugh, no it's still not working.  I was having trouble at the discovery site as well, but now that is working, but that original game link is not.  It works fine on the Mac OS computer next to me.  Strange.

---

### Post by Sirellyn on 2011-05-29
Yeah it must be something with their site. I got another version of if to play on another site.  I'll take it up with them.  Thank you for all your help!

---

### Post by lovinglinux on 2011-05-29
> **Sirellyn said:**
> Yeah it must be something with their site. I got another version of if to play on another site.  I'll take it up with them.  Thank you for all your help!

You are welcome.

---

### Post by 13east on 2011-05-29
> **lovinglinux said:**
> You could try to disable hardware acceleration. Right-click on a Youtube video and select "Settings".

-turned off hardware acceleration for youtube... although i've never had any problems so far w/ youtube itslef... megavideo.com is one of the sites that is still giving me problems

---

### Post by pabc on 2011-06-06
I'm on 64bit 10.04 and have used it today to try and force and update due to the XSS vuln ( [http://www.theregister.co.uk/2011/06/06/flash_security_update/](http://www.theregister.co.uk/2011/06/06/flash_security_update/) ) but I'm still showing as having a vulnerable version (10,3,162,29)

If FA can't sort this can anyone tell me how to install the tar.gz from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) ?

---

### Post by lovinglinux on 2011-06-06
> **pabc said:**
> I'm on 64bit 10.04 and have used it today to try and force and update due to the XSS vuln ( [http://www.theregister.co.uk/2011/06/06/flash_security_update/](http://www.theregister.co.uk/2011/06/06/flash_security_update/) ) but I'm still showing as having a vulnerable version (10,3,162,29)

If FA can't sort this can anyone tell me how to install the tar.gz from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) ?

That is because Adobe hasn't updated the 64bit square preview since November. If you are worried about the security of it, then select the stable release from the repository in Flash-Aid installation options. Doing that will install the latest 32bit with 64bit wrapper, which will be updated via package manager automatically when available.

---

### Post by pabc on 2011-06-07
ta muchly. Now on a 'secure' version.

---

### Post by lovinglinux on 2011-06-07
> **pabc said:**
> ta muchly. Now on a 'secure' version.

You are welcome. Keep in mind the security experts discover critical vulnerabilities on Flash all the time. I recommend that you use [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and set it to block Flash and only allow trusted web sites.

---

### Post by JDVyska on 2011-06-09
Alrighty, hopefully I didn't miss some of the obvious fixes above and hopefully someone can help.

I have an older Dell Precision M90 with:
[LIST]
[*]Processor. Intel Core 2 Duo T7200 2 GHz 4MB L2 Cache, 667MHz FSB
[*]RAM: 2GB (don't recall speed atm)
[*]NVIDIA Quadro FX 1500M with 512MB.  [/LIST]

I had an older version of Ubuntu on it (10.4, 64 bit) that I upgraded all the way to 11.04 this week.  I then updated the NVidia drivers, used the Flash-Aid add-in for firefox, and launched in Ubuntu Classic (no effects) mode.  (Unity worked just fine, I just figured I'd disable in case it was interfering.)

Flash was still crazy slow.

So, I figured maybe it's the old 64 vs 32 bit suffering, so I scrapped the OS, rebuilt on 11.04 32 bit, clean install.  I then updated the NVidia drivers, used the Flash-Aid add-in for firefox, and launched in Ubuntu Classic (no effects) mode.  Still, flash is crazy slow.  I made sure to right-click and disable Hardware Acceleration.

But, no progress.  When flash games are running, the CPU nearly pegs, runs solidly 80-95%.  I even tried Chrome out to see if there would be any difference there - no.

In my "Additional Drivers" (jockey?) dialog, there's options for NVIDIA version 173 and current.  I've tried both out, but whenever I enable either, after restart it says the "Driver is activated but not currently in use."

Any theories on how to make Flash behave on this older machine?  I'd really like it to be an Edubuntu laptop for my kiddo, not just slap Windows on it so he can access some PBS games.

I've tried the  Stable and Beta versions.  I've tried exporting the script and running it directly, just to ensure all is well (attached the most recent).  I've run the Stable install after running a 'sudo apt-get purge flashplugin-installer flashplugin-nonfree'.

I've attached the firefox-report for this system.  Any things I can try that I've missed?

---

### Post by lovinglinux on 2011-06-09
> **JDVyska said:**
> In my "Additional Drivers" (jockey?) dialog, there's options for NVIDIA version 173 and current.  I've tried both out, but whenever I enable either, after restart it says the "Driver is activated but not currently in use."

That's your problem.

Try to install nVidia drivers via Synaptic instead of jockey.

---

### Post by JDVyska on 2011-06-09
> **lovinglinux said:**
> That's your problem.

Try to install nVidia drivers via Synaptic instead of jockey.

OK, so, I dropped out of X, killed gdm, x, everything.  Purged the nvidia drivers I had on the machine.  I started up in VESA, used Synaptic to install nvidia-current, ran my xconfig, etc.

Unity, working just fine.  Flash, no dice.  Still no performance improvement (even back under Ubuntu No Effects).

Feeling bold, I downloaded the NVidia 270.41.19 version straight from NVIDIA and did all the above steps with that one instead.

Unity, still doing just fine.  Flash, no improvement.

:(


Edit: Disregard. Going to Windows again.  I'm sure that'll solve it.  Not ideal solution.

---

### Post by Fr33d0m on 2011-06-09
Mint 11 here.  Since you changed the interface, flash-aid is sadly useless to me.  There is no button, and no way to do anything but stare at the preferences.

---

### Post by lovinglinux on 2011-06-10
> **Fr33d0m said:**
> Mint 11 here.  Since you changed the interface, flash-aid is sadly useless to me.  There is no button, and no way to do anything but stare at the preferences.

Right-click on any toolbar, select "Customize", then find the Flash-Aid icon and drag it to any toolbar.  Close the customization dialog, click the Flash-Aid toolbar icon to access the features.

---

### Post by lovinglinux on 2011-07-06
Version 2.1.2 has been released.

**Changelog:**
[LIST]
[*]added compatibility with Firefox 8.0a1
[*]added rule to remove flash installed from sevenmachines ppa
[*]added mouse pointer effects
[*]fixed minor setTimeout issue
[/LIST]

---

### Post by lovinglinux on 2011-07-07
For those experiencing problems on YouTube see [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by lovinglinux on 2011-07-13
Just updated Flash-Aid to get the new Flash 11 Beta, for both 32bit and 64bit. All you need is to execute the Wizard to install. Hardware acceleration and the performance tweak "Override GPU validation" is working on YouTube again. No more black screen.

You will probably receive a Flash-Aid alert tomorrow, since it only checks for updates once a day. But if you run the Wizard today, you can ignore that alert.

---

### Post by lovinglinux on 2011-07-15
Flash-Aid 2.2.0 is available for download. This version introduces important security improvements. The extension now retrieves all flash beta information using SSL authentication. There is no more redirection to Adobe download site from *updates.webgapps.org*, since the download url is retrieved from the update json file. If the SSL authentication fails, then Flash-Aid uses the urls hard-coded in the extension preferences.

There is also a md5sum check in place for beta downloads. The checksum is also obtained from the update json file and if the downloaded file checksum doesn't match, the extension aborts the installation commands. However, removal and tweaks are still performed.

**Changelog**

[LIST]
[*]added SSL authentication for update server download
[*]added md5 hash verification for beta downloads
[*]removed download link redirector
[*]added beta plugin info to Wizard 
[*]fixed minor issues
[/LIST]

---

### Post by lovinglinux on 2011-08-27
Flash-Aid 2.2.1 is available for download. 

**Changelog**

[LIST]
[*]added compatibility with FF 9
[*]added ssl fallback option
[*]fixed leaking global variables 
[*]fixed minor bugs
[/LIST]

---

### Post by mvandemar on 2011-08-27
> **lovinglinux said:**
> 
[LIST]
[*]added compatibility with FF 9
[/LIST]

Wow! You really are thinking ahead, eh? :D

-Michael

---

### Post by lovinglinux on 2011-08-27
> **mvandemar said:**
> Wow! You really are thinking ahead, eh? :D

-Michael

Indeed. Most of the time I rely on Mozilla's automatic bump, but when I need to edit the add-on, I make sure it works with the nightly version and add the compatibility to the code, so I don't need to worry for some time. :-)

---

### Post by mvandemar on 2011-08-27
> **lovinglinux said:**
> Indeed. Most of the time I rely on Mozilla's automatic bump, but when I need to edit the add-on, I make sure it works with the nightly version and add the compatibility to the code, so I don't need to worry for some time. :-)

Those are alphas though, not sure how helpful it is to code against pre-beta releases. 7 is still in beta, and 8 is in alpha, did you test against them as well? Just curious, not planning on upgrading for a while, if they give me the option. Still slightly irked with 6 (although starting to get over it now that flash is working better than it was when i first installed it).

-Michael

---

### Post by lovinglinux on 2011-08-27
> **mvandemar said:**
> Those are alphas though, not sure how helpful it is to code against pre-beta releases. 7 is still in beta, and 8 is in alpha, did you test against them as well? Just curious, not planning on upgrading for a while, if they give me the option. Still slightly irked with 6 (although starting to get over it now that flash is working better than it was when i first installed it).

-Michael

Yes, I have tested on those as well. The advantage for me is that when they become beta, I don't need to rely on AMO automatic bump or to edit the extension compatibility again and release another version. 

The automatic bump is a great thing, but for some reason I am not aware, when you execute Flash-Aid 2.1.1 on Firefox 6, it loses the compatibility patch bumped automatically by AMO. I have no idea why, but if the extension was already coded with the compatibility, this problem wouldn't occur I wouldn't need to release a new version.

---

### Post by raamee on 2011-09-11
I have installed your extension and it installed. But I can't view youtube video in firefox, it looks grey.

[IMG]http://i.imgur.com/MkzXX.png[/IMG]

Any solution? Firefox version is 6.0.2

---

### Post by lovinglinux on 2011-09-11
> **raamee said:**
> I have installed your extension and it installed. But I can't view youtube video in firefox, it looks grey.

[IMG]http://i.imgur.com/MkzXX.png[/IMG]

Any solution? Firefox version is 6.0.2

Please click the Help menu, generate a report and post it here.

---

### Post by HeroKing on 2011-09-12
running the recent version that was updated a few days ago. on firefox 6.0.2. every time i visit duelingnetwork.com my flash crashes after about 2-5 minutes of activity. this only happened after the latest revision, and i've tried both the stable and beta options of adobe flash that are available

[http://i53.tinypic.com/k83mt.png](http://i53.tinypic.com/k83mt.png)

---

### Post by SigEp418 on 2011-09-12
After downloading FLASH-AID I run the program.  It does it's thing but when the terminal box comes up it will not let me type in my password.  A stand alone terminal will allow input when opened.

I am running 11.04 Natty on a 64-bit system.  Browser in Firefox 6.0.1

:confused:

Flash has never worked on this system.

---

### Post by Steeperton on 2011-09-12
> **SigEp418 said:**
> After downloading FLASH-AID I run the program.  It does it's thing but when the terminal box comes up it will not let me type in my password.  A stand alone terminal will allow input when opened.

I am running 11.04 Natty on a 64-bit system.  Browser in Firefox 6.0.1

:confused:

Flash has never worked on this system.

When inputting your password in terminal, it doesn't display anything for security. Just type, then press enter, and it'll work fine.

---

### Post by raamee on 2011-09-12
> **lovinglinux said:**
> Please click the Help menu, generate a report and post it here.



Attached is my generated report. Thanks. Btw, youtube works in other browsers. It is only in firefox it doesn't works.

---

### Post by SigEp418 on 2011-09-12
> **Steeperton said:**
> When inputting your password in terminal, it doesn't display anything for security. Just type, then press enter, and it'll work fine.

Figured that out a little after I posted.  Thank you!

---

### Post by lovinglinux on 2011-09-13
> **HeroKing said:**
> running the recent version that was updated a few days ago. on firefox 6.0.2. every time i visit duelingnetwork.com my flash crashes after about 2-5 minutes of activity. this only happened after the latest revision, and i've tried both the stable and beta options of adobe flash that are available

[http://i53.tinypic.com/k83mt.png](http://i53.tinypic.com/k83mt.png)

There are no recent changes in Flash-Aid that could cause such problem. Only the Flash version has changed. However, since the problem also happens with the stable version, than I suspect is Firefox issue.

> **raamee said:**
> Attached is my generated report. Thanks. Btw, youtube works in other browsers. It is only in firefox it doesn't works.

Your report shows that your installation is fine and Firefox is detecting the new Flash properly. However, you have an additional *mint-flashplugin-10.3* package installed. It doesn't seem to be detected by Firefox, but you could try to remove it.

Try to disable GPU validation override in Flash-Aid when running the Wizard or disabling hardware acceleration by right-clicking on the video and selecting the Settings option.

---

### Post by raamee on 2011-09-14
> **lovinglinux said:**
> There are no recent changes in Flash-Aid that could cause such problem. Only the Flash version has changed. However, since the problem also happens with the stable version, than I suspect is Firefox issue.



Your report shows that your installation is fine and Firefox is detecting the new Flash properly. However, you have an additional *mint-flashplugin-10.3* package installed. It doesn't seem to be detected by Firefox, but you could try to remove it.

Try to disable GPU validation override in Flash-Aid when running the Wizard or disabling hardware acceleration by right-clicking on the video and selecting the Settings option.

I un-installed that and did that. But still the grey thing is there :( . Any other solution? should I report this to firefox? 

Thanks.

---

### Post by lovinglinux on 2011-09-14
> **raamee said:**
> I un-installed that and did that. But still the grey thing is there :( . Any other solution? should I report this to firefox? 

Thanks.

First, check if it works on other flash based video web sites. It might be an YouTube issue. If other sites work, try to delete the cookies and the cache, then block YouTube cookies to see if it works.

---

### Post by raamee on 2011-09-15
> **lovinglinux said:**
> First, check if it works on other flash based video web sites. It might be an YouTube issue. If other sites work, try to delete the cookies and the cache, then block YouTube cookies to see if it works.

Sorry, no flash thingy is working. All the flash videos on all the sites looks grey.

---

### Post by lovinglinux on 2011-09-16
> **raamee said:**
> Sorry, no flash thingy is working. All the flash videos on all the sites looks grey.

Try [https://www.youtube.com](https://www.youtube.com)

---

### Post by raamee on 2011-09-17
> **lovinglinux said:**
> Try [https://www.youtube.com](https://www.youtube.com)

Still grey :(

---

### Post by raamee on 2011-09-18
Filed a bug in firefox: 

[https://bugzilla.mozilla.org/show_bug.cgi?id=687346]("https://bugzilla.mozilla.org/show_bug.cgi?id=687346")

---

### Post by elstud1 on 2011-09-18
use "Lightspark" for flash player from software center i have an older machine with 512 mg ram and 80 g hard drive works great for me

---

### Post by lovinglinux on 2011-09-18
> **raamee said:**
> Still grey :(

Please try a clean Firefox profile.

---

### Post by raamee on 2011-09-26
> **lovinglinux said:**
> Please try a clean Firefox profile.

Thanks for your help :) I removed the RGBA. Now it works.

---

### Post by lovinglinux on 2011-12-08
Flash-Aid 2.2.2 has been released!

[LIST]
[*]added the extension menu to the Tools menu
[*]added option to check for flash updates manually
[*]added option to install 64bit version from partner repository
[*]added flashplugin-downloader removal
[*]added compatibility with Firefox 11
[*]HWVideo Decode disabled by default, to avoid issues in recent flash versions
[*]removed swfdec from advanced installation options
[*]added lightspark to advanced installation options
[*]fixed issue with custom installation using downloaded package
[/LIST]

---

### Post by franckt on 2011-12-28
I've been using your add-on fo a while and was satisfied. Beginning of this week, I did an update on my Ubuntu Natty concerning firefox (from version 8 to 9). I don't have any problem with flash except on this page : [www.playtv.fr/television/france-24]("http://www.playtv.fr/television/france-24")  (I have a problem with all the TV shows, I did write previously one of the links available)
Anyone can tell me if he can see this TV show with FF 9 ? 
I can see it... but after 10 seconds or sometimes 4mn, FF crashes.

Thanks and enjoy the end of 2011

---

### Post by lovinglinux on 2011-12-30
> **franckt said:**
> I've been using your add-on fo a while and was satisfied. Beginning of this week, I did an update on my Ubuntu Natty concerning firefox (from version 8 to 9). I don't have any problem with flash except on this page : [www.playtv.fr/television/france-24]("http://www.playtv.fr/television/france-24")  (I have a problem with all the TV shows, I did write previously one of the links available)
Anyone can tell me if he can see this TV show with FF 9 ? 
I can see it... but after 10 seconds or sometimes 4mn, FF crashes.

Thanks and enjoy the end of 2011

No problems with that video on a 32bit system.

Run Flash-Aid Wizard again and disable GPU Validation and HWVideo Decode is they are selected. Execute the script, restart Firefox and test the video again.

---

### Post by Sijmen on 2011-12-30
Awesome! This solved flash control and buffering issues. Thanks a bunch! :D

---

### Post by franckt on 2011-12-30
I've done this but with no success. FInally I did downgrade FF to version 8 and it works.

---

### Post by Frogs Hair on 2012-01-25
Hello LL 

The menu in Flash Aid 2.2.2 disappears as  soon release the icon . I have to hold the left mouse button down in order to navigate the menu . I was able to update  flash player today and I don't remember this behavior before .

 I am using Nightly , so if nothing can be done that's fine . I have recently deleted my .moziilla  folder and reinstalled all my add-ons including the Nightly Tester Tools .  As always thanks for your time .

---

### Post by lovinglinux on 2012-01-27
> **Frogs Hair said:**
> Hello LL 

The menu in Flash Aid 2.2.2 disappears as  soon release the icon . I have to hold the left mouse button down in order to navigate the menu . I was able to update  flash player today and I don't remember this behavior before .

 I am using Nightly , so if nothing can be done that's fine . I have recently deleted my .moziilla  folder and reinstalled all my add-ons including the Nightly Tester Tools .  As always thanks for your time .

This must be an issue with the nightly. Have you tried the new Tools menu?

---

### Post by Derek Karpinski on 2012-01-27
lovinglinux,
 
Have you had any problems with the new beta release of flash 64 bit?  Flash-aid informed me that a new version was available, and I installed it, then all the videos on youtube were tinted blue.
 
I had to back down to the version in the repositories......but now I can't use HW acceleration.
 
Any ideas?  Thanks for a great FF plugin!

---

### Post by Frogs Hair on 2012-01-27
> **lovinglinux said:**
> This must be an issue with the nightly. Have you tried the new Tools menu?

The tools menu works fine it's just the icon which I really don't need . I stick to the beta  version of flash and don't change unless there is an update .

---

### Post by lovinglinux on 2012-01-28
> **Derek Karpinski said:**
> lovinglinux,
 
Have you had any problems with the new beta release of flash 64 bit?  Flash-aid informed me that a new version was available, and I installed it, then all the videos on youtube were tinted blue.
 
I had to back down to the version in the repositories......but now I can't use HW acceleration.
 
Any ideas?  Thanks for a great FF plugin!

HW acceleration has been disabled in recent versions of Flash. No info when it will be enabled again.

> **Frogs Hair said:**
> The tools menu works fine it's just the icon which I really don't need . I stick to the beta  version of flash and don't change unless there is an update .

In this case, you can remove the icon from the toolbar and use the Tools menu only.

---

### Post by Frogs Hair on 2012-02-02
> **lovinglinux said:**
> HW acceleration has been disabled in recent versions of Flash. No info when it will be enabled again.



In this case, you can remove the icon from the toolbar and use the Tools menu only.

The Flash Aid icon menu is working fine with Nightly 13.0a1 so far .

---

### Post by missingno222 on 2012-02-07
> **HeroKing said:**
> running the recent version that was updated a few days ago. on firefox 6.0.2. every time i visit duelingnetwork.com my flash crashes after about 2-5 minutes of activity. this only happened after the latest revision, and i've tried both the stable and beta options of adobe flash that are available

[http://i53.tinypic.com/k83mt.png](http://i53.tinypic.com/k83mt.png)

 I'm having this same problem.  I really want to access Dueling Network, but can't.  I don't know if this makes a difference, but, I have tried both Opera and Chromium to no avail.  Was the only solution to donwgrade Firefox to version 8.0?

---

### Post by Linux Dutchman on 2012-02-07
I've noticed that since a few days youtube becomes slow, it's lagging and now and then freezes when using full screen. Some online game sites i visit (for example: [www.spele.nl]("http://www.spele.nl")) some games doesn't show up.
 
Whats wrong here??

---

### Post by lovinglinux on 2012-02-07
> **Linux Dutchman said:**
> I've noticed that since a few days youtube becomes slow, it's lagging and now and then freezes when using full screen. Some online game sites i visit (for example: [www.spele.nl]("http://www.spele.nl")) some games doesn't show up.
 
Whats wrong here??

I am not sure. But I suspect it could be due to the fact that recent versions of flash don't support hardware acceleration. Did you upgrade flash or Firefox recently?

---

### Post by Linux Dutchman on 2012-02-07
Recently Canonical provided an update for Firefox from FF 3.xx to FF 10.0. I had the Mozilla Stable PPA added, but after this update through Canonical i deleted that PPA. Also for Thunderbird.
 
Since this update i'm experiencing problems of Flash not working properly. After that i did an update on my Flash using that Flash-aid tool just to check. Even this trick: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia/freezing-flash-solution](https://sites.google.com/site/tipsandtricksforubuntu/multimedia/freezing-flash-solution) didn't work for me.

---

### Post by lovinglinux on 2012-02-07
> **Linux Dutchman said:**
> Recently Canonical provided an update for Firefox from FF 3.xx to FF 10.0. I had the Mozilla Stable PPA added, but after this update through Canonical i deleted that PPA. Also for Thunderbird.
 
Since this update i'm experiencing problems of Flash not working properly. After that i did an update on my Flash using that Flash-aid tool just to check. Even this trick: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia/freezing-flash-solution](https://sites.google.com/site/tipsandtricksforubuntu/multimedia/freezing-flash-solution) didn't work for me.

Do you have any other browser installed, so you can test if the problem is localized?

---

### Post by Linux Dutchman on 2012-02-07
> **lovinglinux said:**
> Do you have any other browser installed, so you can test if the problem is localized?

No. I only use FF.

Which browser do i need to install to test this?

---

### Post by lovinglinux on 2012-02-07
> **Linux Dutchman said:**
> No. I only use FF.

Which browser do i need to install to test this?

Try Chromium

---

### Post by fdmille on 2012-02-07
Flash-Aid just fixed my problems.  Thanks a bunch! :popcorn:

---

### Post by lovinglinux on 2012-02-08
> **fdmille said:**
> Flash-Aid just fixed my problems.  Thanks a bunch! :popcorn:

You are welcome.

---

### Post by Linux Dutchman on 2012-02-08
> **lovinglinux said:**
> Try Chromium

Still the same. Video is lagging.

---

### Post by lovinglinux on 2012-02-09
> **Linux Dutchman said:**
> Still the same. Video is lagging.

So I think is the flash inability to render videos using hardware acceleration in recent versions.

---

### Post by lovinglinux on 2012-02-11
[COLOR="Red"][SIZE="4"]**IMPORTANT!**[/SIZE][/COLOR]

I have uploaded version 2.2.3 to GitHub and Mozilla. Please update as soon as possible, since the previous version will stop working next week.

This update is not available through Firefox yet, neither through the extension home page. You need to get from one of the links below:

[https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi](https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi)

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/)


The most important changes in this version:

[LIST]
[*]the extension no longer check for new flash versions on start, except after the first install. So you need to check manually, through the "Check Update" option in the extension menu.

[*]the extension is using GitHub now for downloading the update check json file
[/LIST]

---

### Post by teejay17 on 2012-02-13
> **lovinglinux said:**
> [COLOR=Red][SIZE=4]**IMPORTANT!**[/SIZE][/COLOR]

I have uploaded version 2.2.3 to GitHub and Mozilla. Please update as soon as possible, since the previous version will stop working next week.

This update is not available through Firefox yet, neither through the extension home page. You need to get from one of the links below:

[https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi](https://github.com/downloads/webgapps/flashaid/flash-aid-2.2.3-fx-linux.xpi)

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/)


The most important changes in this version:

[LIST]
[*]the extension no longer check for new flash versions on start, except after the first install. So you need to check manually, through the "Check Update" option in the extension menu.
[*]the extension is using GitHub now for downloading the update check json file
[/LIST]

Will it eventually become available via Firefox?

---

### Post by lovinglinux on 2012-02-13
> **teejay17 said:**
> Will it eventually become available via Firefox?

Yes, it will, once a Mozilla editor review it. Shouldn't take long.

I have extended my web site hosting contract for a month, so the current version of Flash-Aid will still work for another 30 days, unless they turn my site off. They were threatening to do so, due to server overload.

---

### Post by Joentokyo on 2012-02-14
Flashaid works very well, but recently I have to run it every time I close and open Firefox. What am I doing wrong?

---

### Post by lovinglinux on 2012-02-14
> **Joentokyo said:**
> Flashaid works very well, but recently I have to run it every time I close and open Firefox. What am I doing wrong?

Why do you need to do that? What happens if you don't?

---

### Post by Joentokyo on 2012-02-14
> **lovinglinux said:**
> Why do you need to do that? What happens if you don't?

If I don't run Flashaid each time I reopen Firefox then I cannot play flash videos or any other file that uses flash.

Today I used the terminal to delete  /usr/lib/mozilla/plugins/libflashplayer.so and  /user/ob/firefox-addons/plugins/libflashplayer.co before running Flashaid to see if I got a better result, but I have closed Firefox yet, so I do not know if that helped.

Another issue is that when I run Flashaid and close Firefox after closing the terminal, Firefox does not restart automatically and I am back at my homepage when I reopen it.

Will let you know if I have better results this time.

---

### Post by Joentokyo on 2012-02-15
I have closed Firefox and reopened a couple of times, not in a row to test this, but in normal use. No problems now.

---

### Post by lovinglinux on 2012-02-15
> **Joentokyo said:**
> I have closed Firefox and reopened a couple of times, not in a row to test this, but in normal use. No problems now.

So, is it solved?

---

### Post by Joentokyo on 2012-02-16
> **lovinglinux said:**
> So, is it solved?

Yes, I am only guessing, but I think the problem was that the old files were not being removed when I ran the app.

---

### Post by lovinglinux on 2012-02-17
> **teejay17 said:**
> Will it eventually become available via Firefox?

It has been approved by Mozilla and is now available through Firefox add-on update.

---

### Post by Joentokyo on 2012-02-19
> **lovinglinux said:**
> It has been approved by Mozilla and is now available through Firefox add-on update.

I am only guessing, but I think it is possible that usr/lib/mozilla/plugins/libflashplayer.so and  /user/ob/firefox-addons/plugins/libflashplayer.so were installed twice, and maybe in different location, and that caused the problem.

---

### Post by ACGilbert on 2012-02-20
Using Flash-aid I have installed flash version 11.2.202.197 (latest beta) and it is giving me intermittant black screen w/sound and no video.
I have tried to go back to 11.1.102.62 (latest stable) using wizard, quick and advanced modes of flash-aid without any luck. The terminal window says it is installing 11.1.102.62, but when I close and restart Firefox the beta version still shows in add-ons/plugins and on the Adobe Flash test page on the web.
I am running Ubuntu 3.0.0-16 64 bit on a quad core AMD, 8 gigs ram, and an NVIDIA GT240 with driver version 295.20.

Thanks for your time,

AC

---

### Post by lovinglinux on 2012-02-20
> **ACGilbert said:**
> Using Flash-aid I have installed flash version 11.2.202.197 (latest beta) and it is giving me intermittant black screen w/sound and no video.
I have tried to go back to 11.1.102.62 (latest stable) using wizard, quick and advanced modes of flash-aid without any luck. The terminal window says it is installing 11.1.102.62, but when I close and restart Firefox the beta version still shows in add-ons/plugins and on the Adobe Flash test page on the web.
I am running Ubuntu 3.0.0-16 64 bit on a quad core AMD, 8 gigs ram, and an NVIDIA GT240 with driver version 295.20.

Thanks for your time,

AC

Start the Advanced mode and set it the way you did before, then copy and paste the generated script here. Also, click "Help >> Generate REport" and paste here.

---

### Post by IPEX-731BA5DD06 on 2012-02-20
I've installed your flash-aid it solved my problems with Youtube videos and 
the newspaper I also read online.

My problem is trying to install RabbitVCS it keeps crashing saying I need to 
configure flashplayer and flashplugin.

I've generated the report you've mentioned, and its showing they aren't configured.

How do I configure them?. I've tried removing RabbitVCS, installing reinstalling
installing through command line, Ubuntu software centre and via Synaptic. 

all crash giving the same result. I've uninstalled flash and re-installed.

Problem occurred when I was originally installing RabbitVCS and modem went off 
line, it won't recover from that crash??

How do I configure flashplayer and flashplugin?? it works, but not configured?




Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) /usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) /etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat

Thanks in advance, sorry to jump in (not really, I'm extremely frustrated)

---

### Post by ACGilbert on 2012-02-20
> **lovinglinux said:**
> Start the Advanced mode and set it the way you did before, then copy and paste the generated script here. Also, click "Help >> Generate REport" and paste here.

Thanks for the reply -- here's the script and Report.
AC

Script:

```
#!/bin/bash

sudo apt-get --yes purge adobe-flashplugin
sudo apt-get update
sudo apt-get --yes install adobe-flashplugin
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'OverrideGPUValidation')
if test -z "${TWEAK}";then
echo 'OverrideGPUValidation=true' | sudo tee -a /etc/adobe/mms.cfg
fi
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'EnableLinuxHWVideoDecode')
if test -z "${TWEAK}";then
echo 'EnableLinuxHWVideoDecode=1' | sudo tee -a /etc/adobe/mms.cfg
fi
NPVIEWER=/usr/lib/nspluginwrapper/i386/linux/npviewer
if test -f "${NPVIEWER}";then
cat /usr/lib/nspluginwrapper/i386/linux/npviewer | sed '/export GDK_NATIVE_WINDOWS=1/d' | sudo tee /usr/lib/nspluginwrapper/i386/linux/npviewer
fi


```

Report:```
Ubuntu Architecture

Linux papa-desktop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-10.0.2/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

danielrichter2007-grub-customizer___Add_Source___Close_Reload-natty.list
danielrichter2007-grub-customizer___Add_Source___Close_Reload-natty.list.save
danielrichter2007-grub-customizer-natty.list.distUpgrade
danielrichter2007-grub-customizer-natty.list.save
danielrichter2007-grub-customizer-oneiric.list
danielrichter2007-grub-customizer-oneiric.list.save
myunity-ppa-oneiric.list
stebbins-handbrake-releases-natty.list.distUpgrade
stebbins-handbrake-releases-natty.list.save
stebbins-handbrake-releases-oneiric.list
stebbins-handbrake-releases-oneiric.list.save
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.save
ubuntu-wine-ppa-natty.list.distUpgrade
ubuntu-wine-ppa-natty.list.save
ubuntu-wine-ppa-oneiric.list
ubuntu-wine-ppa-oneiric.list.save
ubuntu-x-swat-x-updates-oneiric.list
ubuntu-x-swat-x-updates-oneiric.list.save
weather-indicator-team-ppa-natty.list.distUpgrade
weather-indicator-team-ppa-natty.list.save
weather-indicator-team-ppa-oneiric.list
weather-indicator-team-ppa-oneiric.list.save

Flash packages

adobe-flash-properties-gtk			install
adobe-flashplugin				install
Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1327288872000:1:5:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:4:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318915705000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$

[INVALID]


```

---

### Post by lovinglinux on 2012-02-21
> **ACGilbert said:**
> Thanks for the reply -- here's the script and Report.
AC

I am not sure why it isn't detecting the beta and removing it. I couldn't reproduce the problem.

Run this to fix it:


```
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by lovinglinux on 2012-02-21
> **IPEX-731BA5DD06 said:**
> I've installed your flash-aid it solved my problems with Youtube videos and 
the newspaper I also read online.

My problem is trying to install RabbitVCS it keeps crashing saying I need to 
configure flashplayer and flashplugin.

You keep  get an error in the terminal? Does it offer a possible solution? If yes, then try it.

---

### Post by ACGilbert on 2012-02-21
> **lovinglinux said:**
> I am not sure why it isn't detecting the beta and removing it. I couldn't reproduce the problem.

Run this to fix it:


```
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
```

lovinglinux,
Thanks again. I now have 11.1.102.62 being reported by Firefox!
AC

---

### Post by lovinglinux on 2012-02-21
> **ACGilbert said:**
> lovinglinux,
Thanks again. I now have 11.1.102.62 being reported by Firefox!
AC

You are welcome.

---

### Post by IPEX-731BA5DD06 on 2012-02-22
ON my problem, its been solved.

I just re-installed the Rabbitvcs files x2 from Synaptic again, and it went through fine this time.

Its actually working, I don't know what I did, maybe it was one of the removals and a reboot that did it.

Anyway Thanks for you reply, but most of all, THANKS FOR THIS THREAD, and Flash aid program you wrote

---

### Post by lovinglinux on 2012-02-22
> **IPEX-731BA5DD06 said:**
> ON my problem, its been solved.

I just re-installed the Rabbitvcs files x2 from Synaptic again, and it went through fine this time.

Its actually working, I don't know what I did, maybe it was one of the removals and a reboot that did it.

Anyway Thanks for you reply, but most of all, THANKS FOR THIS THREAD, and Flash aid program you wrote

You are welcome.

---

### Post by lovinglinux on 2012-02-22
**Adobe Abandons Flash on Linux**

[http://ubuntuforums.org/showthread.php?p=11709219#post11709219](http://ubuntuforums.org/showthread.php?p=11709219#post11709219)

---

### Post by Automatic Slim on 2012-02-22
The above news notwithstanding, I've registered in order to thank lovinglinux for providing me with the means to resolve my Flash problems.  I'm very much obliged to you, sir.

---

### Post by lovinglinux on 2012-02-22
> **Automatic Slim said:**
> The above news notwithstanding, I've registered in order to thank lovinglinux for providing me with the means to resolve my Flash problems.  I'm very much obliged to you, sir.

You are welcome. 

About the news, it seems we will still get security updates, but new major versions won't be released.

---

### Post by evil gnome on 2012-02-23
I want to install flash player for **Chromium**
I'm running Lubuntu 11.10
Please Help

```
xxx@xxx-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-downloader' instead of 'flashplugin-nonfree'
flashplugin-downloader is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 14:47:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 14:47:12 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lovinglinux on 2012-02-23
> **evil gnome said:**
> I want to install flash player for **Chromium**
I'm running Lubuntu 11.10
Please Help

```
xxx@xxx-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-downloader' instead of 'flashplugin-nonfree'
flashplugin-downloader is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 14:47:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 14:47:12 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Have you tried Flash-Aid?

---

### Post by winh8r on 2012-02-23
> **evil gnome said:**
> I want to install flash player for **Chromium**
I'm running Lubuntu 11.10
Please Help

```
xxx@xxx-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-downloader' instead of 'flashplugin-nonfree'
flashplugin-downloader is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 14:47:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 14:47:12 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I directed you to this thread from your original post, if you read the very first entry in this thread , posted by lovinglinux there is a link to install Flash-Aid which will almost certainly solve your problem.

---

### Post by evil gnome on 2012-02-23
I opened the link (In firefox) and clicked "Add to firefox" button. but the download progress bar doesn't start at all (and yes my internet connection is up and running, I can surf the Mozilla website alright)

That's weird.
Is there any other way to download Flash-aid? like an offline installer file.

---

### Post by evil gnome on 2012-02-23
> **evil gnome said:**
> I opened the link (In firefox) and clicked "Add to firefox" button. but the download progress bar doesn't start at all (and yes my internet connection is up and running, I can surf the Mozilla website alright)

That's weird.
Is there any other way to download Flash-aid? like an offline installer file.
OH in the time I was writing this post, the download started and finished.

---

### Post by evil gnome on 2012-02-23
OK I executed Flash-Aid and it didn't work
This is the result:

```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
[sudo] password for xxx: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release
Hit http://archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://archive.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted Sources
Hit http://archive.ubuntu.com oneiric/universe Sources
Hit http://archive.ubuntu.com oneiric/multiverse Sources
Hit http://archive.ubuntu.com oneiric/main i386 Packages
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 17:30:08--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33, 91.189.92.191
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 17:30:09 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```

---

### Post by lovinglinux on 2012-02-23
> **evil gnome said:**
> OK I executed Flash-Aid and it didn't work
This is the result:

```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
[sudo] password for xxx: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release
Hit http://archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://archive.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted Sources
Hit http://archive.ubuntu.com oneiric/universe Sources
Hit http://archive.ubuntu.com oneiric/multiverse Sources
Hit http://archive.ubuntu.com oneiric/main i386 Packages
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 17:30:08--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33, 91.189.92.191
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 17:30:09 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```


For some reason, the package manager is trying to download flash 11.0.1.152 while the currently available version is 11.1.102.62. 

Try to change the download server through the Software Sources application.

---

### Post by evil gnome on 2012-02-23
> **lovinglinux said:**
> For some reason, the package manager is trying to download flash 11.0.1.152 while the currently available version is 11.1.102.62. 

Try to change the download server through the Software Sources application.

Changed to a US server, also a Germany server. with no result :(

```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
[sudo] password for untitled: 
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 23:21:43--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 23:21:44 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```

---

### Post by lovinglinux on 2012-02-23
> **evil gnome said:**
> Changed to a US server, also a Germany server. with no result :(

```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
[sudo] password for untitled: 
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 23:21:43--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 23:21:44 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```


Use the Beta version option in Flash-Aid instead of the stable version from the repositories. This will allow to install the latest flash. However, it won't solve the package manager problem. I am not sure why it is trying to get an old version and can't offer a solution. My concern is that it might be trying to get old versions of other packages as well. I suggest you create a new topic to deal with this package manager issue.

---

### Post by evil gnome on 2012-02-24
> **lovinglinux said:**
> Use the Beta version option in Flash-Aid instead of the stable version from the repositories. This will allow to install the latest flash. However, it won't solve the package manager problem. I am not sure why it is trying to get an old version and can't offer a solution. My concern is that it might be trying to get old versions of other packages as well. I suggest you create a new topic to deal with this package manager issue.
[FONT="Courier New"]I'm living in a sanctioned country. macromedia.com won't allow me to download from their server (like sourceforge.com)

EDIT: **[PROBLEM SOLVED]("http://ubuntuforums.org/showpost.php?p=11713743&postcount=7")**[/FONT]

---

### Post by coilwinder on 2012-03-01
Hi, I just wanted to say THANKS for FLASH-AID!

My biggest problem with it was locating the icon on the toolbar to start it:P
Flash seems to be working again, for the second time in a few days, so I hope this lasts a bit longer.


As for my first attempt, this is/was the situation:

After an update about 10 days or so ago, I didn't notice Firefox was marked to be updated too, and I didn't want the new one. Uninstalled that, and then proceeded to just "install" an older version (simply extracting it) in my home folder/firefox.

Also, I diverted the innstallation path of firefox like this:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s ~/firefox/firefox /usr/bin/firefox

```Using a symbolic link it seems, what the dpkg arguments are for I'm not sure.

Just FYI, that can be reverted like this:

```
sudo unlink /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox

```I got Ubuntu 10.04 LTS 64-bit, but I'm actually as of this writing not  sure what "bit version" of firefox I got.. I guess it's a 32-bit  version, the only flash player that would work was also a 32 bit version  (downloaded firefox-3.6.27.tar.bz2 from [http://www.mozilla.org/en-US/firefox/all-older.html](http://www.mozilla.org/en-US/firefox/all-older.html) )

I put the flash player files/folders in my home folder/firefox/plugins (again simply extracted it there. 32-bit tar.gz file from [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/) ). 

And that actually worked! Well for a few days. I have no idea why it stopped working.

---

### Post by lovinglinux on 2012-03-01
> **coilwinder said:**
> Hi, I just wanted to say THANKS for FLASH-AID!

My biggest problem with it was locating the icon on the toolbar to start it:P
Flash seems to be working again, for the second time in a few days, so I hope this lasts a bit longer.

You are welcome.

Please keep in mind Firefox 3.6 will reach end-of-life on April 24th. Continuing to use it will be a security risk. I strongly advise you to use Firefox 10 from the repositories.

---

### Post by dsmithnc on 2012-03-02
Followed your directions, installed and ran plug-in.  No luck.

Here is output:

About Firefox:

Firefox 10.0.2 Mozilla Firefox for Ubuntu
canonical - 1.0

uname -a
Linux ****-Satellite-L505D 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

locate libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

Thanks
****

---

### Post by lovinglinux on 2012-03-02
> **dsmithnc said:**
> Followed your directions, installed and ran plug-in.  No luck.

Here is output:

About Firefox:

Firefox 10.0.2 Mozilla Firefox for Ubuntu
canonical - 1.0

uname -a
Linux ****-Satellite-L505D 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

locate libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

Thanks
****

What exactly is your issue? I can't find the original post right now.

Please click the Help menu in Flash-Aid, generate a report and post here.

---

### Post by dsmithnc on 2012-03-02
The Report:

Ubuntu Architecture

Linux ****-Satellite-L505D 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-10.0.2/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

atareao-atareao-oneiric.list
atareao-atareao-oneiric.list.save
conscioususer-polly-unstable-oneiric.list
conscioususer-polly-unstable-oneiric.list.save
dlynch3-ppa-oneiric.list
dlynch3-ppa-oneiric.list.save
google-chrome.list
google-chrome.list.save
google-musicmanager.list
google-musicmanager.list.save
hotot-team-ppa-oneiric.list
hotot-team-ppa-oneiric.list.save
kamalmostafa-fldigi-oneiric.list
kamalmostafa-fldigi-oneiric.list.save
matthaeus123-mrw-gimp-svn-oneiric.list
matthaeus123-mrw-gimp-svn-oneiric.list.save
serge-hallyn-vimprobable-oneiric.list
serge-hallyn-vimprobable-oneiric.list.save
techm3-outrec-oneiric.list
techm3-outrec-oneiric.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.save

Flash packages

Plugin locations

/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libgnome-shell-browser-plugin.so:$
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so:$
:$
1330602142000:1:1:$
This plugin provides integration with Gnome Shell for live extension enabling and disabling. It can be used only by extensions.gnome.org:$
Gnome Shell Integration:$
1
0:application/x-gnome-shell-integration:Gnome Shell Integration Dummy Content-Type::$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1329915900000:1:1:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1329915900000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.3.90 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1329915900000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.3.90 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.3.90):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-vegas-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-vegas-plugin.so:$
:$
1329915900000:1:1:$
Shockwave Flash 11.1 r102:$
Shockwave Flash:$
1
0:application/x-shockwave-flash:Shockwave Flash:swf:$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1329915900000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.3.90 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
6
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
5:application/vnd.apple.mpegurl:HTTP Live Streaming playlist:m3u8:$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1326079387000:1:5:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1321905447000:1:13:$
Shockwave Flash 11.2 d202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]

---

### Post by lovinglinux on 2012-03-02
> **dsmithnc said:**
> The Report:

Ubuntu Architecture

Linux ****-Satellite-L505D 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

It is a bug caused by Totem plugin. Open the add-on Manager, click the plugin section and check if you see a Vegas Totem plugin and disable it.

---

### Post by dsmithnc on 2012-03-02
> **lovinglinux said:**
> It is a bug caused by Totem plugin. Open the add-on Manager, click the plugin section and check if you see a Vegas Totem plugin and disable it.


Found the following.  Disabled all. restarted Firefox, no luck.

QuickTime Plug-in 7.6.6 (disabled)
The Totem 3.3.90 plugin handles video and audio streams.

VLC Multimedia Plug-in (compatible Totem 3.3.90)(disabled)
The Totem 3.3.90 plugin handles video and audio streams

Windows Media Player Plug-in 10 (compatible; Totem)(disabled)
The Totem 3.3.90 plugin handles video and audio streams

---

### Post by lovinglinux on 2012-03-03
> **dsmithnc said:**
> Found the following.  Disabled all. restarted Firefox, no luck.

QuickTime Plug-in 7.6.6 (disabled)
The Totem 3.3.90 plugin handles video and audio streams.

VLC Multimedia Plug-in (compatible Totem 3.3.90)(disabled)
The Totem 3.3.90 plugin handles video and audio streams

Windows Media Player Plug-in 10 (compatible; Totem)(disabled)
The Totem 3.3.90 plugin handles video and audio streams

Try this:

```
sudo apt-get purge totem-mozilla
sudo apt-get install gecko-mediaplayer
```

This will remove totem plugin and install gecko-mediaplayer in it's place.


BTW, I hope you are not complaining about Adobe Air applications, because Adobe Air use it's own flash player. Different solution needed. What exactly is your problem with flash?

---

### Post by dsmithnc on 2012-03-03
> **lovinglinux said:**
> Try this:

```
sudo apt-get purge totem-mozilla
sudo apt-get install gecko-mediaplayer
```

This will remove totem plugin and install gecko-mediaplayer in it's place.


BTW, I hope you are not complaining about Adobe Air applications, because Adobe Air use it's own flash player. Different solution needed. What exactly is your problem with flash?

No, it doesn't have to do with Adobe Air.  I cannot see any online video content since I solved the problem with Gimp.  I can't see videos with Firefox or Google Chrome.

Thanks for you patience with this.

****

---

### Post by lovinglinux on 2012-03-14
I have just updated the flash version. To get the new version, click "Check Update" in the extension menu, wait for the alert about the new version, then run the Wizard again.

---

### Post by lovinglinux on 2012-03-14
Important information for nVidia users:

[QUOTE=pqwoerituytrueiwoq]There is a known issue with flash 11.2 and nvidia on youtube

works: unchecked + EnableLinuxHWVideoDecode=0
color fail: checked + EnableLinuxHWVideoDecode=0
unstable: checked + EnableLinuxHWVideoDecode=1 
unstable: unchecked + EnableLinuxHWVideoDecode=1                                  

the checked status revers to this
[IMG]http://i.imgur.com/1ZBra.png[/IMG]

color fail refers to the inversion of red and blue

This will info will be useful for your flash add addon

Adobe has basically said they will not fix it cause they don't support linux any more (even though they do for this version)

adobe bug report ids 3097844, 3077076, and 3109467[/QUOTE]

---

### Post by pqwoerituytrueiwoq on 2012-03-14
There is a known issue with flash 11.2 and Nvidia on youtube (and possibly other sites)

works: unchecked + EnableLinuxHWVideoDecode=0
color fail: checked + EnableLinuxHWVideoDecode=0
unstable: checked + EnableLinuxHWVideoDecode=1 
unstable: unchecked + EnableLinuxHWVideoDecode=1

the checked status revers to this
[IMG]http://i.imgur.com/1ZBra.png[/IMG]

color fail refers to the inversion of red and blue colors

This will info will be useful for your flash add addon

Adobe has basically said they will not fix it cause they don't support linux anymore (even though they officially do for this version)

adobe bug report ids 3097844, 3077076, and 3109467

---

### Post by Steeperton on 2012-03-15
> **pqwoerituytrueiwoq said:**
> There is a known issue with flash 11.2 and Nvidia on youtube (and possibly other sites)

works: unchecked + EnableLinuxHWVideoDecode=0
color fail: checked + EnableLinuxHWVideoDecode=0
unstable: checked + EnableLinuxHWVideoDecode=1 
unstable: unchecked + EnableLinuxHWVideoDecode=1

the checked status revers to this
[IMG]http://i.imgur.com/1ZBra.png[/IMG]


When I right click on a flash video, and select "settings", this settings box pops-up, but is unresponsive - I can't do anything with it, including closing! So I have to refresh the page to view the video! 11.10 x64, if that makes a difference. And yes, I have the YouTube Smurf thing going on :(

---

### Post by lovinglinux on 2012-03-15
> **Steeperton said:**
> When I right click on a flash video, and select "settings", this settings box pops-up, but is unresponsive - I can't do anything with it, including closing! So I have to refresh the page to view the video! 11.10 x64, if that makes a difference. And yes, I have the YouTube Smurf thing going on :(

Please click Flash-Aid "Help" menu, select "Generate Report" and post it here.

---

### Post by lovinglinux on 2012-03-15
> **Steeperton said:**
> When I right click on a flash video, and select "settings", this settings box pops-up, but is unresponsive - I can't do anything with it, including closing! So I have to refresh the page to view the video! 11.10 x64, if that makes a difference. And yes, I have the YouTube Smurf thing going on :(

Try [http://forums.adobe.com/message/3863047#3863047](http://forums.adobe.com/message/3863047#3863047)

---

### Post by Steeperton on 2012-03-20
> **lovinglinux said:**
> Try [http://forums.adobe.com/message/3863047#3863047](http://forums.adobe.com/message/3863047#3863047)

Afriad not - clicking on the version number, the "settings" option is greyed out :(

> **lovinglinux said:**
> Please click Flash-Aid "Help" menu, select "Generate Report" and post it here.
Ta.

---

### Post by lovinglinux on 2012-03-21
> **Steeperton said:**
> Afriad not - clicking on the version number, the "settings" option is greyed out :(


Ta.


Type **about:addons** in the address bar, click plugins. Find Gnome Shell Browser Pluguin and disable it. Try again.

---

### Post by lovinglinux on 2012-03-31
> **Steeperton said:**
> Afriad not - clicking on the version number, the "settings" option is greyed out :(


Ta.


Try this:

> **mc4man said:**
> I'd go with an older flash version but if you wish to disable hw acceleration in the flash settings you must do it in the player while it's  in fullscreen
(scrollbars make the settings box unclickable


If that doesn't work, then try this:

Open /etc/adobe/mms.cfg with an editor using admin privileges.

```
gksudo gedit /etc/adobe/mms.cfg
```

Add this line:

```
EnableLinuxHWVideoDecode=1
```

Restart Firefox.

If that doesn't work, try to delete the flash config file:

```
sudo rm -f /etc/adobe/mms.cfg
```

Also see [http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

.

---

### Post by mikodo on 2012-04-01
Hi Lovinglinux,

I'm all but sure you talked about this issue already, but I cannot find it, and cannot remember what you had said.

I read somewhere in this thread that we should manually be updating the Flash-Aid add-on extension through the add-on manual update process. I did that, then tried to watch some Adobe flash videos, and was prompted to install Adobe Plugin 11.2.202.228.org.tar.gz. I allowed it to install and the Flash Video played.

I then thought I would try Flash-Aid (2.2.3); and ran the Wizard mode for stable flash, and beta 32 Bit flash (11.2.202.183), and in both instances, it removed the flashplugin-installer (I assume the one above). When trying to play the flash video, I would have to install the above Adobe plugin again, to be able to watch the flash video.

I don't remember going through this before, Flash-Aid, just looked after it.

Can you shed some light on this?

Thanks.

---

### Post by lovinglinux on 2012-04-01
> **mikodo said:**
> Hi Lovinglinux,

I'm all but sure you talked about this issue already, but I cannot find it, and cannot remember what you had said.

I read somewhere in this thread that we should manually be updating the Flash-Aid add-on extension through the add-on manual update process. I did that, then tried to watch some Adobe flash videos, and was prompted to install Adobe Plugin 11.2.202.228.org.tar.gz. I allowed it to install and the Flash Video played.

I then thought I would try Flash-Aid (2.2.3); and ran the Wizard mode for stable flash, and beta 32 Bit flash (11.2.202.183), and in both instances, it removed the flashplugin-installer (I assume the one above). When trying to play the flash video, I would have to install the above Adobe plugin again, to be able to watch the flash video.

I don't remember going through this before, Flash-Aid, just looked after it.

Can you shed some light on this?

Thanks.

Hi mikodo,

On previous versions of Flash-Aid, every day you started Firefox for the first time, it would check if a new beta version of Flash was available and alert you. I had to remove that behavior, because it was putting too much pressure on the server, since Flash-Aid has about 32.000 daily users. Now, you need to click the "Check Update" menu entry, which queries the server for date of release of the current beta. If the date of release on the server is higher than the one stored by the extension, it alerts you that a new version is available and stores the new download url. So when you run the wizard again, it will fetch the new flash version.

The "Check Update" feature doesn't consider changes in the stable versions from repositories, since updates are offered automatically through the package manager.

Currently, Flash-Aid is offering version 11.2.202.221, which was the last beta (b6) delivered by Adobe. The current stable version from the official repositories is 11.2.202.228, which is the version that is causing issues to nVidia users.

I am not sure why the web site is forcing you to install 11.2.202.228, but this has nothing to do with Flash-Aid. It is probably an issue with a particular web site. I am running version 11.2.202.221 just fine here, with several web sites.

Please type **[noparse]about:config[/noparse]** in the address bar, type **extensions.flashaid.remotedata** in the search filter, then right-click the resulting preference, select the option "Copy Value" and post here. Do the same for **extensions.flashaid.dataupdate**.

---

### Post by mikodo on 2012-04-01
I have a feeling this is not what you are wanting, but I cannot find "copy value".

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=extensions.flashaid.remotedata&hl=en#gsc.tab=0&gsc.q=extensions.flashaid.remotedata&gsc.page=1
```

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=extensions.flashaid.dataupdate&hl=en#gsc.tab=0&gsc.q=extensions.flashaid.dataupdate&gsc.page=1
```

---

### Post by lovinglinux on 2012-04-01
> **mikodo said:**
> I have a feeling this is not what you are wanting, but I cannot find "copy value".

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=extensions.flashaid.remotedata&hl=en#gsc.tab=0&gsc.q=extensions.flashaid.remotedata&gsc.page=1
```

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=extensions.flashaid.dataupdate&hl=en#gsc.tab=0&gsc.q=extensions.flashaid.dataupdate&gsc.page=1
```

This is what I need:

---

### Post by mikodo on 2012-04-01
> **lovinglinux said:**
> This is what I need:
I can't open that Thumbnail

---

### Post by lovinglinux on 2012-04-01
> **mikodo said:**
> I can't open that Thumbnail

[http://ubuntuforums.org/attachment.php?attachmentid=215287&d=1333320639](http://ubuntuforums.org/attachment.php?attachmentid=215287&d=1333320639)

---

### Post by mikodo on 2012-04-01
Thanks for the help lovinglinux, but I am sick today, and am not concentrating well, and now must go.

I will try to follow your directions later.

All my best,

Mike

---

### Post by lovinglinux on 2012-04-01
> **mikodo said:**
> Thanks for the help lovinglinux, but I am sick today, and am not concentrating well, and now must go.

I will try to follow your directions later.

All my best,

Mike

Okay. Get well.

---

### Post by mikodo on 2012-04-01
I think this is what you wanted. Unfortunately, I do need to go. :( 

```
{"flashbeta32":[{"timestamp":"20120119","version":"11.2.202.183","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p4_install_lin_32_011912.tar.gz","hash":"7ba6da7b0525c48819d2a06c7f3eab05"}],"flashbeta64":[{"timestamp":"20120119","version":"11.2.202.183","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p4_install_lin_64_011912.tar.gz","hash":"1fa02e0c8313082a63ce1e17d3386190"}]}
``````
20120211
```

---

### Post by lovinglinux on 2012-04-01
> **mikodo said:**
> I think this is what you wanted. Unfortunately, I do need to go. :( 

```
{"flashbeta32":[{"timestamp":"20120119","version":"11.2.202.183","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p4_install_lin_32_011912.tar.gz","hash":"7ba6da7b0525c48819d2a06c7f3eab05"}],"flashbeta64":[{"timestamp":"20120119","version":"11.2.202.183","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p4_install_lin_64_011912.tar.gz","hash":"1fa02e0c8313082a63ce1e17d3386190"}]}
``````
20120211
```

Replace the value first one with this:

```
{"flashbeta32":[{"timestamp":"20120227","version":"11.2.202.221","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p6_install_lin_32_022712.tar.gz","hash":"adb63f230ee1cff45e7be2ccd58664ac"}],"flashbeta64":[{"timestamp":"20120227","version":"11.2.202.221","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p6_install_lin_64_022712.tar.gz","hash":"08bcfbbe196a2d2e4d1f7258b48532e8"}]}
```

Then run the wizard again.

---

### Post by mikodo on 2012-04-01
> **lovinglinux said:**
> Replace the value first one with this:

```
{"flashbeta32":[{"timestamp":"20120227","version":"11.2.202.221","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p6_install_lin_32_022712.tar.gz","hash":"adb63f230ee1cff45e7be2ccd58664ac"}],"flashbeta64":[{"timestamp":"20120227","version":"11.2.202.221","url":"http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p6_install_lin_64_022712.tar.gz","hash":"08bcfbbe196a2d2e4d1f7258b48532e8"}]}
```Then run the wizard again.Thank you.

That fixed the problem.

---

### Post by lovinglinux on 2012-04-05
Adobe purged the last beta from the server. So now Flash-Aid Beta feature is delivering the same version that is available in the repos. The one causing the SMURF effect. Not much I can do about it, since I am not allowed to distribute Flash directly.

I will rename the Beta feature to something else in the next version of Flash-Aid. Meanwhile, it will continue delivering the versions Adobe let us.

---

### Post by lovinglinux on 2012-04-14
I have updated Flash-Aid download url to get flash version 11.2.202.233. If you want that version, click "Check Update" in the extension menu, wait for the warning that a new version is available and then run the Wizard again, selecting the BETA option.

Unfortunately, this version still causes SMURF effect on nVidia powered machines.

---

### Post by Jaguarandine on 2012-07-09
I've been working on my aunt's old computer that runs Lubuntu 12.04. After the 12.04 update, Flash stopped working. I tried Flash Aid, but for some reason it doesn't work. Do you think you could help me with my problem? Thanks!

---

### Post by claracc on 2012-07-10
You have to download an old adobe flash plugin which works for you i.e.: 11.1 release or 10.3.183.20 ( that is what I am using in my old pentium III with sis 630/730 graphics card and lubuntu 12.04, because the 11.2 release crahses all my web browsers).

You can download old adobe flash from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), if you download a zip file you have to unzip and choose the .tar.gz suitable for linux, then it can be used the lovinglinux flash-aid add-on for firefox in its "custom" way in order to install the old adobe flash plugin.

Note that using an old adobe flash plugin can have security risks

---

### Post by Jaguarandine on 2012-07-10
Okay thanks! I'll try it out.

---

### Post by Jaguarandine on 2012-07-11
Thanks! That did the trick! One less headache ;)

On an off-topic note, how do you get flash to not run like garbage on an old computer? My 69 yr old aunt puts up with it because she loves her old machine. I've tried prioritizing the flash process with the "renice" command, but that doesn't seem like something my aunt can do herself. The machine is an old Vaio, PIII 800 MHz, 512 RAM w/ Lubuntu 12,04. Any tips?

Thanks again for your help!

---

### Post by claracc on 2012-07-11
Well, to run flash videos in such an old machines (pentium III) is a real pain and I think is a little beyond its posibilities since adobe flash plugin is a resources hog.

What can work for you is to use flashvideoreplacer addon for firefox (lovinglinux is the author), but it only can be run in certain sites [https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/), or you can try to use a low resources cunsumption web browser.

Other solutions can be to download the flash videos (jdownloader perhaps) convert to avi and watch them in smplayer.

---

### Post by kolaff on 2012-08-09
I noticed the add-on was removed from the Mozilla repository, can you explain the reason why? 
 
Edit: Ok read on the site it was discountinued because of Adobe's choice

---

### Post by photosyn on 2012-08-15
So is there another way to get Flash-Aid now?  
Thanks for the reply.

---

### Post by lovinglinux on 2012-08-17
> **kolaff said:**
> I noticed the add-on was removed from the Mozilla repository, can you explain the reason why? 
 
Edit: Ok read on the site it was discountinued because of Adobe's choice

Among other things, because of the end of support for Flash on Linux, because I am currently unable to fix bugs and provide support. This decision is not final tho. I am still deciding what to do.


> **photosyn said:**
> So is there another way to get Flash-Aid now?  
Thanks for the reply.

Yes. You can get it from GitHub at [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

However, keep in mind it might not work as expected.

---

### Post by photosyn on 2012-08-18
Thanks for the reply, lovinglinux.  I very much appreciate the service you have provided to all of us in supplying Flash-Aid for so long.  It has made things very workable for novice Linux users like me.  Take care.

---

### Post by vasa1 on 2012-08-18
> **photosyn said:**
> thanks for the reply, lovinglinux.  I very much appreciate the service you have provided to all of us in supplying flash-aid for so long.  It has made things very workable for novice linux users like me.  Take care.

+1.

---

### Post by lovinglinux on 2012-08-20
> **photosyn said:**
> Thanks for the reply, lovinglinux.  I very much appreciate the service you have provided to all of us in supplying Flash-Aid for so long.  It has made things very workable for novice Linux users like me.  Take care.

> **vasa1 said:**
> +1.

Hey guys. I am considering porting Flash-Aid to GTK. It would be a lot easier to maintain than a Firefox add-on. But I would have to limit the functionality, since there are no more Beta flash versions. 

The main issue tho is that I need to learn Python first. ;)

I have been exploring Quickly in the last few days and it seems very easy to work with. So I will try to find some time for this project. 

Stay tuned.

---

### Post by Sylslay on 2012-08-20
Hi,

Can  You post some sort of script for optimiaze flash while installing it from Ubuntu repos.

Like override GPU settinegs etc...?

On last fiew laptops I used flash-aid, 
and it does the great job!!

I am using old freind netbook now and he is very sad that He can t watch
youtube at 360p, (since inslalled on new faster pendrive - hdd is out of order)

I am just to lazy to tune firefox with other howtos, but had to run this [http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

flash-aid works great on older celenron machine.


Cheers
):P

Thanks for flash-aid.
Do Yoo know how to transfer add-on from one machine to other?

---

### Post by lovinglinux on 2012-08-21
> **Sylslay said:**
> Hi,

Can  You post some sort of script for optimiaze flash while installing it from Ubuntu repos.

Like override GPU settinegs etc...?

On last fiew laptops I used flash-aid, 
and it does the great job!!

I am using old freind netbook now and he is very sad that He can t watch
youtube at 360p, (since inslalled on new faster pendrive - hdd is out of order)

I am just to lazy to tune firefox with other howtos, but had to run this [http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

flash-aid works great on older celenron machine.


Cheers
):P

Thanks for flash-aid.
Do Yoo know how to transfer add-on from one machine to other?


You are welcome.


You can still use Flash-Aid to install Flash from the repos. Just select that option in the wizard.

You can still get flash-aid from [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

However, if you want to transfer it, then just copy/paste ~/.mozilla/firefox/xxxxxx.Default/extensions/flashaid@lovinglinux.megabyet.net folder from your profile to the new one.

---

### Post by tamccullough on 2012-08-22
Hey lovinglinux...

Why hasn't canonical hired you to handle flash for them?  It might actually work properly if they did.  :)

---

### Post by sanktjohanser on 2012-08-23
Hi lovinglinux,

I have a quick and possibly dumb question that I have not been able to find an answer to. I am one week old into Linux and am on a steep learning curve here so bear with me.

I have been trying to get flash to work on my g4 powerbook 5,4 running ubuntu 10,10 and firefox 11. I have had zero success!

I managed to find and download your plugin but the question is whether it would work with my machine and if so - how do I install it?

Any help you could offer would be greatly appreciated - even just pointing me in the right direction or just letting me know to totally give up and live without flash would be ok.

Thanks in advance!

---

### Post by lovinglinux on 2012-08-23
> **tamccullough said:**
> Hey lovinglinux...

Why hasn't canonical hired you to handle flash for them?  It might actually work properly if they did.  :)

I apprecciate the suggestion, but I am not a good programmer. Don't tell anyone, but Mozilla add-on editors pull their hair off when they see my clumsy code. ;-)

---

### Post by lovinglinux on 2012-08-23
> **sanktjohanser said:**
> Hi lovinglinux,

I have a quick and possibly dumb question that I have not been able to find an answer to. I am one week old into Linux and am on a steep learning curve here so bear with me.

I have been trying to get flash to work on my g4 powerbook 5,4 running ubuntu 10,10 and firefox 11. I have had zero success!

I managed to find and download your plugin but the question is whether it would work with my machine and if so - how do I install it?

Any help you could offer would be greatly appreciated - even just pointing me in the right direction or just letting me know to totally give up and live without flash would be ok.

Thanks in advance!

Drag the downloaded xpi file to a Firefox window and follow the instructions to install flash-aid. After installing and restarting the browser, start Flash-Aid wizard from the toolbar or tools menu. In the installation options, select the stable version from the repositories (the beta doesn't exist anymore) and complete the Wizard to install flash.

---

### Post by sanktjohanser on 2012-08-24
Thank you very much lovinglinux.

The weird thing is when I choose the stable release the script tells me it's not available - and when I choose the beta, it installs the plugin but my browser still tells me that I am missing the plugin ;(

Any ideas? As I said I am on a powerpc, could this have anything to do with it?

---

### Post by lovinglinux on 2012-08-24
> **sanktjohanser said:**
> Thank you very much lovinglinux.

The weird thing is when I choose the stable release the script tells me it's not available - and when I choose the beta, it installs the plugin but my browser still tells me that I am missing the plugin ;(

Any ideas? As I said I am on a powerpc, could this have anything to do with it?

Go to [http://get.adobe.com/br/flashplayer/?no_redirect](http://get.adobe.com/br/flashplayer/?no_redirect)

Copy the url of the *tar.gz* file corresponding to your system architecture. Start Flash-Aid in*Advanced Mode*, select *Custom* in the installation options and paste the copied url. Execute the script.

---

### Post by twhilden7 on 2012-08-27
for some reason before the addon was taken off the addon list for FF flash aid worked fine for me...after that i have installed it from git  and run it fine but when i go to youtube it doesn't even show a black square where the video should be. i remember at one point before i found out about flash aid i downloaded an older lib*.so file and replaced the current one and that made it work fine ... any help or anyone know where to get the .so file again?? thanks in advance.

---

### Post by lovinglinux on 2012-08-27
> **twhilden7 said:**
> for some reason before the addon was taken off the addon list for FF flash aid worked fine for me...after that i have installed it from git  and run it fine but when i go to youtube it doesn't even show a black square where the video should be. i remember at one point before i found out about flash aid i downloaded an older lib*.so file and replaced the current one and that made it work fine ... any help or anyone know where to get the .so file again?? thanks in advance.

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by lovinglinux on 2012-09-08
**IMPORTANT**

I have updated Flash-Aid to work with Firefox 15 and temporarily re-enabled the extension on AMO site.

I will try to keep it running until I can port it to Python/GTK.

---

### Post by astrobob.tk on 2012-11-26
I had been using the Flash-Aid addon for quite a long time & it has done a great job.

Not sure why, but youtube stopped working recently. A video plays for a few seconds (like 7 secs) before it stops. Moreover, selecting some other time on the vid also breaks it.
I am getting a "An error occurred. Please try again later".

I tried a lot of things: cleared cache, cookies, blocked youtube cookies. Tried all versions of flash in the Flash-Aid wizard, disabled the GPU validation.

Nothing worked. This also affects chrome!

could you please help?

Note: I tried it on a fresh installation in Vbox (with & without Flash-Aid) & it works!

---

### Post by photosyn on 2012-11-27
Hi there.  I'm not sure why you are having trouble but you could try an older version of Firefox?  I know some real old ones don't work even with flashaid.  V15 should work -- I got V17 to work but that was probably pure dumb luck.  Adobe ought to work with Chrome though in any version so maybe that is not the problem.  But something you could check.  If I think of more I'll send it later. Good luck.

---

### Post by astrobob.tk on 2012-11-27
> **photosyn said:**
> Hi there.  I'm not sure why you are having trouble but you could try an older version of Firefox?  I know some real old ones don't work even with flashaid.  V15 should work -- I got V17 to work but that was probably pure dumb luck.  Adobe ought to work with Chrome though in any version so maybe that is not the problem.  But something you could check.  If I think of more I'll send it later. Good luck.

FF updated some time ago to V17 just like yours; i have the ppa i guess. If it works for you (& in a vbxo out of the box without flashaid) it ought to work with me :(

I tried safe mode but the problem persists!

Installing an older version? That's a bit annoying; I don't wish to lose anything or have to backup/restore my customizations :(

Let me know of any ideas. Thanks

---

### Post by monkeybrain2012 on 2012-11-27
> **astrobob.tk said:**
> I had been using the Flash-Aid addon for quite a long time & it has done a great job.

Not sure why, but youtube stopped working recently. A video plays for a few seconds (like 7 secs) before it stops. Moreover, selecting some other time on the vid also breaks it.
I am getting a "An error occurred. Please try again later".

I tried a lot of things: cleared cache, cookies, blocked youtube cookies. Tried all versions of flash in the Flash-Aid wizard, disabled the GPU validation.

Nothing worked. This also affects chrome!

could you please help?

Note: I tried it on a fresh installation in Vbox (with & without Flash-Aid) & it works!

 Did you try other sites than Youtube?

---

### Post by Dural on 2012-12-16
I am using Ubuntu 12.04 64-bit. I have a recourring problem with Flash where if I play videos on Youtube for a while eventually my whole system freezes. Sometimes I can get back to the console and restart lightdm and then login again but other times I have to power off my system in order to get everything back to normal again. Would Flash-Aid help in dealing with this? I installed the latest verion of flash with a system update and I don't want to risk messing anything up.

Hardware:
GPU - Nvidia GeForce 9800GT Mobile
Processor - Intel Core 2 Duo @ 2.40 Ghz
Drivers -  Nvidia version-experimental 304 (believe these were the most recent drivers that would work on my system; think I installed them in November)

I should note that this problem happened even when I used the Nouveau drivers that were initially installed with my system. It also happened whether I used Unity2D or Gnome Classic.

---

### Post by Rfdp on 2012-12-23
I use Firefox 17.0.1 and Chromium [COLOR=#303942][FONT=Ubuntu]20.0.1132.47[/FONT][/COLOR] on a Ubuntu 12.04 64-bit version.

Until yesterday all flash videos worked fine, but after I followed these [https://sites.google.com/site/easylinuxtipsproject/firefox](https://sites.google.com/site/easylinuxtipsproject/firefox) instructions, I have no sound on either Firefox or Chromium.

I tried to install gnash instead, which didn't help, and used Flash-aid 2.2.3, but the problem remains the same.

about:plugins showsshockwave as well as Java, VLC an QuickTime plugin. Should I disable any of these?

What else could I try to get the audio working again for flash?
Thanks for the help


Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-35-generic
GNOME 3.4.2

---

### Post by vasa1 on 2012-12-23
> **Rfdp said:**
> ...
Until yesterday all flash videos worked fine, but after I followed these [https://sites.google.com/site/easylinuxtipsproject/firefox](https://sites.google.com/site/easylinuxtipsproject/firefox) instructions, I have no sound on either Firefox or Chromium.
...
Why did you follow those instructions if flash was working for you?

---

### Post by Rfdp on 2012-12-23
Because I wanted to configure Firefox in an acceptable way

---

### Post by xp15 on 2013-06-04
There is a problem with installing the beta version (the download source is not good) and only the stable flash version is available.
I tried to contuct lovinglinux but failed, can anyone tell him? or give his email?

also, any news abput flash-aid?

---

### Post by oldos2er on 2013-06-05
As noted in post #300, flash aid is no longer supported because flash itself is no longer supported on Linux.

---

### Post by xp15 on 2013-06-05
> **oldos2er said:**
> As noted in post #300, flash aid is no longer supported because flash itself is no longer supported on Linux.

No, I talked with him this year. or a bit before. How can I contuct him? I dont care to use the last flash available to linux. I will use any version.
FLASH-AID is a fantastic tool, which makes the flash work better! a lot! lovinglinux just should to return the beta flash to the source, because FLASH-AID cant find it.
I use the stable now, but feel it is not so good as the beta.

How can i talkl to lovinglinux? I need him.

---

### Post by oldos2er on 2013-06-05
Only way I know to contact him is through [https://github.com/webgapps](https://github.com/webgapps)

---

### Post by xp15 on 2013-06-07
Thanks!

---

