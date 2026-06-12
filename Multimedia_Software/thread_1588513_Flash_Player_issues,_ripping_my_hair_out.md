---
title: "Flash Player issues, ripping my hair out"
date: 2010-10-05
forum: Multimedia Software
---

### Post by Eric7772000 on 2010-10-05
I'll make this as brief as possible, but this is what has happened so far:

I upgraded my OS to Ubuntu 10.04, like it so far but somewhere along the line the Flash Player went completely awry.
I logged onto Hulu and Slash and it told me I have to upgrade my Flash Player. 
I upgraded my Flash Player, went back to Hulu, Slash and You Tube and got video but no audio.
I restarted the system and logged back onto Hulu and Slash, and it once again told me I need to upgrade my Flash Player.  
I logged back onto You Tube and got video but no audio.  
My synaptic package manager tells me that my Flash Player is version 10.01, which is the exact version I'm being told I need to upgrade to.  System says it's working perfectly.
I tried the same with another browser (Epiphany) and got the same results. My main browser is Firefox 3.6.10
My system plays all sound effects, mp3s, CDs and other audio files just fine, so I know my sound card is working.
I've tried everything I can think of, to no avail.  Really aggravated... Can someone please help me?

---

### Post by teresaejunior on 2010-10-05
The website does a wrong verification, thinking that everyone in the world uses the Windows version of Adobe Flash, or even worse, some websites think everyone uses Internet Explorer. Or even worse, the website doesn't work even in Internet Explorer with Adobe Flash!

Some web browsers allow you to change the browser Identification. I can remember now Konqueror, Midori, some addon for Firefox, I think Opera also does. You might try identifying your browser as Internet Explorer, but since they are doing some odd check on Flash, maybe a hard thing to solve.

It doesn't mean your flash won't work. You could try contacting the Webmasters.

Best regards!
Teresa e Junior

EDIT: I didn't catch the audio thing, but you can always try removing the flash from adobe and installing Gnash or Swfdec.

---

### Post by TBABill on 2010-10-05
Do you have all codecs installed or just Flash? If you didn't do it already, install ubuntu-restricted-extras from the Software Center or Synaptic. You may have to uninstall Flash and reinstall as well if something corrupted.

---

### Post by Old_Man_Unix on 2010-10-05
Follow this URL to determine if Flash is installed correctly and which version you have

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)


The current version is 10.1.85.3.

If you don't have that version, or if you do and it is malfunctioning, I would remove whatever you have and then install the *ubuntu-restricted-extras* metapackage as recommended by TBABill.

The free replacements for Flash as mentioned by [teresaejunior]("http://ubuntuforums.org/member.php?u=991572") are unfortunately not very good at this point.

---

### Post by efflandt on 2010-10-05
Does Firefox under Tools > Add-ons show it as Shockwave Flash 10.1 r85 (or anything different or others)?  Even the 32-bit version of that with nswrapper that flashplugin-installer for 64-bit Lucid works fine for me on an older system for 64-bit Hulu Desktop.

On a newer PC manually installed real 64-bit flash that shows up as 10.2 r161 also works fine with 64-bit Hulu Desktop.

However, those were Lucid installed from scratch.  When I upgraded 32-bit 9.10 to 10.04, flashplugin-nonfree and flashplugin-installer appeared to be installed, but Firefox did not show any flash plugin, Hulu Desktop could not find flash, and ubuntu-restricted-extras showed as not installed.    Even after uninstalling flashplugin-nonfree and installing ubuntu-restricted-extras, nothing showed up for flash in Firefox until I marked flashplugin-installer to reinstall.  Then Shockwave Flash 10.1 r85 showed up in Firefox and Hulu Desktop worked without telling it where flash was.

So you might just need to mark flashplugin-installer for reinstallation, and apply.

---

### Post by Eric7772000 on 2010-10-05
This is what I have tried so far:
downloading and installing the tarball, seems to be successful, but Firefox/tools/add-ons still says 9.0 r124.
installing adobe flash through the synaptic package manager, which says it has been successfully installed.  Synaptic package manager says I'm successfully running 10.1.85.3-1lucid1.  Firefox add-ons still says 9.0 r124.
Installed Ubuntu restricted extras, flashplugin-installer, re-installed 10.1.85 from synaptic...all say it has been successfully installed, but firefox still says 9.0 r124.

what am I doing wrong?

oh, and how do I change the way my browser is identified?

---

### Post by lovinglinux on 2010-10-05
> **Eric7772000 said:**
> This is what I have tried so far:
downloading and installing the tarball, seems to be successful, but Firefox/tools/add-ons still says 9.0 r124.
installing adobe flash through the synaptic package manager, which says it has been successfully installed.  Synaptic package manager says I'm successfully running 10.1.85.3-1lucid1.  Firefox add-ons still says 9.0 r124.
Installed Ubuntu restricted extras, flashplugin-installer, re-installed 10.1.85 from synaptic...all say it has been successfully installed, but firefox still says 9.0 r124.

what am I doing wrong?

oh, and how do I change the way my browser is identified?

The problem is because you still has Gnash installed, which is the flash plugin being detected by Firefox. removed it to fix the issue.

```
sudo apt-get purge mozilla-plugin-gnash
```

If that doesn't work, then get FLASH-AID version 1.0.14:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

---

### Post by Eric7772000 on 2010-10-05
Unfortunately, neither of those helped either.  Firefox still shows 9.0 r124.  The terminal said Gnash wasn't installed so it didn't need to be removed, downloaded and installed Flash Aid, but that didn't seem to do anything.  

I'm thinking I need to go in and remove version 9 completely, but I don't know how to do that.  Synaptic says I still have 10.1.85.3, successfully installed, but firefox still says 9.0 r124.

---

### Post by lovinglinux on 2010-10-05
> **Eric7772000 said:**
> The terminal said Gnash wasn't installed so it didn't need to be removed, downloaded and installed Flash Aid, but that didn't seem to do anything. 

After installing FLASH-AID and restarting Firefox, it will automatically prompt for flash installation, showing which version will be installed, according to your system architecture. After clicking OK, it will display which commands will be executed and after clicking OK again it will launch a Terminal and execute the commands to remove conflicting plugins and install the proper version of flash. If that didn't happen, then click the FLASH-AID icon on the toolbar and select the "Install" option. If you are using a 64bit system, make sure you get FLASH-AID 1.0.14, because version 1.0.13 is broken due to changes in the 64bit url made by Adobe recently.

Do you get any errors in the terminal?

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

### Post by nomanslan369 on 2010-10-05
Maybe it could be the 32bit and 64bit problem like I was having... check out this link...

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by Eric7772000 on 2010-10-05
I hope this is what you need...Thank you so MUCH for your help!

Part 1:

**Shockwave Flash**

 File: /usr/lib/firefox-addons/plugins/libflashplayer.so     
Version: Shockwave Flash 10.2 d161                                                                 
MIME Type                                    Description                 Suffixes         Enabled
application/x-shockwave-flash         Shockwave Flash        swf                Yes
application/futuresplash                  FutureSplash Player     spl                Yes
                             
Part 2:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

Part 3:
Ubuntu Architecture  Linux Ericseldest 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"  

Firefox Packages 
 firefox                        install 
firefox-2                     deinstall 
firefox-3.0                  deinstall 
firefox-branding           install  

Firefox binaries 
 /usr/bin/firefox 
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion 

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory) 

Sources 

Flash packages 

adobe-flashplugin                   install 
flashplugin-installer                deinstall 
libflash0c2                             deinstall  

Plugin locations 

/home/eric/.mozilla/plugins/libflashplayer.so 
/home/eric/install_flash_player_9_linux/libflashplayer.so 
/usr/lib/adobe-flashplugin/libflashplayer.so 

/usr/lib/firefox/plugins/flashplugin-alternative.so 
/usr/lib/iceape/plugins/flashplugin-alternative.so 
/usr/lib/iceweasel/plugins/flashplugin-alternative.so 
/usr/lib/midbrowser/plugins/flashplugin-alternative.so 
/usr/lib/mozilla/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so 

Flash symlinks 

/usr/lib/firefox-addons/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)  
 

I hope this is what you were looking for...honestly, it makes no sense to me. :-)  Again, thank you so much for your help!

---

### Post by .... on 2010-10-05
Maybe you should search your filesystem for libflashplayer.so ...

---

### Post by .... on 2010-10-05
> /home/eric/.mozilla/plugins/libflashplayer.so 
/home/eric/install_flash_player_9_linux/libflashplayer.so 
/usr/lib/adobe-flashplugin/libflashplayer.so 

Remove these three files and reinstall the flash package
```
rm ~/.mozilla/plugins/libflashplayer.so
rm ~/install_flash_player_9_linux/libflashplayer.so
sudo rm /usr/lib/adobe-flashplugin/libflashplayer.so 
sudo apt-get install --reinstall flashplugin-installer
```

---

### Post by Eric7772000 on 2010-10-06
That did the trick!!  Works great!  HOORAY!!  Thank You!!

---

### Post by shelmarae on 2010-11-08
[SIZE=3]**1**[/SIZE]
Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type     Description     Suffixes     Enabled
application/x-shockwave-flash     Shockwave Flash     swf     Yes
application/futuresplash     FutureSplash Player     spl     Yes


[B][SIZE=3]2
[/SIZE][/B]
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.04 (lucid) Firefox/3.6.12


[SIZE=3]**3**[/SIZE]

Attached

Was having very similar problems to the 9.0 issue from this thread, FLASH-AID still doesn't fix sound from playing.

I also have PulseAudio Chooser and manager installed, when I play a video a very slight like flicker of ALSA plugin shows when flash videos are playing, but no sound at all.

Any help is greatly appreciated.

---

### Post by lovinglinux on 2010-11-08
> **shelmarae said:**
> [SIZE=3]**1**[/SIZE]
Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type     Description     Suffixes     Enabled
application/x-shockwave-flash     Shockwave Flash     swf     Yes
application/futuresplash     FutureSplash Player     spl     Yes


[B][SIZE=3]2
[/SIZE][/B]
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.12) Gecko/20101027 Ubuntu/10.04 (lucid) Firefox/3.6.12


[SIZE=3]**3**[/SIZE]

Attached

Was having very similar problems to the 9.0 issue from this thread, FLASH-AID still doesn't fix sound from playing.

I also have PulseAudio Chooser and manager installed, when I play a video a very slight like flicker of ALSA plugin shows when flash videos are playing, but no sound at all.

Any help is greatly appreciated.

Try to remove flashplugin-nonfree-extrasound:

```
sudo apt-get remove flashplugin-nonfree-extrasound
```

---

