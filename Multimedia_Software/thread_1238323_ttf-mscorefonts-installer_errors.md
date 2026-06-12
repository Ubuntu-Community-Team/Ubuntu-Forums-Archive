---
title: "ttf-mscorefonts-installer errors"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Cossar on 2009-08-12
Hey guys, tried searching around and couldn't find an answer to this problem. Right now I'm trying to work through ubuntu-freak's excellent howto on sound and video because my flash applications have no sound. However, when I try to run scripts I get this error:

```
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This happens when I run any apt-get applications.

---

### Post by kerry_s on 2009-08-12
```
sudo apt-get -f install
```

---

### Post by Cossar on 2009-08-12
This is what I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kerry_s on 2009-08-12
are you using a proxy?

---

### Post by Cossar on 2009-08-13
No. That's why it's so weird..

---

### Post by sblunix on 2009-08-13
I had this exact same problem as well when trying to install flashplugin-nonfree... IDK why! >:( I ended up doing a full system reinstall because I need flash...

---

### Post by kerry_s on 2009-08-13
> **Cossar said:**
> No. That's why it's so weird..

check the system network settings, make sure it's not set to auto proxy.

---

### Post by Cossar on 2009-08-13
Checked the Network Proxy, and it was set to auto proxy so I set it to direct connection. I rebooted, but I still get that error.

---

### Post by jeegiz on 2009-08-14
I had the same problem, i guess it is related to the automatic proxy settings. But after i set it back to direct connection, it still did not work.

I got it working after i removed ttf-mscorefonts-installer.deb file from the /var/cache/apt/archives folder, so apt had to download package again.

---

### Post by Cossar on 2009-08-15
Sweet, thanks for the fix. This is a dumb question, but I get an "access denied" notification when I try to delete it, even though I gave Active console authorizations for all the options in Authorizations. Do I have to add explicit authorizations for my user?

---

### Post by alex sun on 2009-09-01
For me this error appears for direct connection and after deleting corresponding packages in /var/cache/apt/archives folder
Nothing helps :(
Ubuntu is running in VirtualBox.

Edit: restart helped :)

---

### Post by murias002 on 2009-09-06
hi. I was in the same error during 2 hours, looking for a solution in so many websites and forums, but, never, nothing... after thing about, i found my problem.

My problem was because i am using endian firewall, and i turned on the option "restrict browsers for access internet", then, i selected firefox, get, apt, etc., but, during the ttf-mscorefonts install process, the core of ubuntu try downloading other files directly, and them the endian firewall cut the communications and deny the download process hidden in the installation sequence.

The solution was uncheck the internet browser restriction during installation or during apt-get install ttf-mscorefonts process, and great, work very fine. For this reason ubuntu not has this issue like a bug, because not is a bug, is a very particular firewall configuration.

probably the same condition are you looking in another firewall too, because usually we have obtaining the major protection possible, and some time this is bad for us.

thanks a lot, i hope help in the solution. thanks.

---

### Post by xieqiao on 2009-09-06
try this code

sudo apt-get remove ttf-mscorefonts-installer

---

### Post by ellaguno on 2009-09-14
Thanks

Removing the ttf-mscorefonts-installer solved my problem.

---

### Post by boehr on 2009-10-12
I had been having problems with the **ttf-mscorefonts-installer** package for days! Synaptic's repeated efforts to update the package were futile and frustrating. There were no solutions posted on the internet that seemed to work for me - below is the only solution that did the trick.

[SIZE="2"]Step 1 - Get the fonts manually[/SIZE]
I found all the fonts in .exe form at [http://web.nickshanks.com]("http://web.nickshanks.com/fonts/microsoft-core-web-fonts"). Download all of them.

[INDENT]:arrow: Thank you very much, Nicholas Shanks![/INDENT]

[SIZE="2"]Step 2 - Relocate the fonts[/SIZE]
Use gksudo Nautilus to copy or move all the .exe files to **/etc/apt**.

[SIZE="2"]Step 3 - Use Synaptic[/SIZE]
Find the **ttf-mscorefonts-installer** package and mark it for reinstallation. Hit apply. 

[SIZE="2"]Step 4 - Smile[/SIZE]

---

### Post by Cossar on 2009-10-14
Finally fixed it! Thanks so so much to those who helped...it was bugging me for so long.

---

### Post by e-Gee on 2009-10-15
No Smile for me where you put this fonts in etc/apt

---

### Post by rimmer74 on 2009-10-22
> **boehr said:**
> I had been having problems with the **ttf-mscorefonts-installer** package for days! Synaptic's repeated efforts to update the package were futile and frustrating. There were no solutions posted on the internet that seemed to work for me - below is the only solution that did the trick.

[SIZE="2"]Step 1 - Get the fonts manually[/SIZE]
I found all the fonts in .exe form at [http://web.nickshanks.com]("http://web.nickshanks.com/fonts/microsoft-core-web-fonts"). Download all of them.

[INDENT]:arrow: Thank you very much, Nicholas Shanks![/INDENT]

[SIZE="2"]Step 2 - Relocate the fonts[/SIZE]
Use gksudo Nautilus to copy or move all the .exe files to **/etc/apt**.

[SIZE="2"]Step 3 - Use Synaptic[/SIZE]
Find the **ttf-mscorefonts-installer** package and mark it for reinstallation. Hit apply. 

[SIZE="2"]Step 4 - Smile[/SIZE]

I have followed these instructions but to no avail - still getting that error message. Any help please?

---

### Post by boehr on 2009-10-24
> **rimmer74 said:**
> I have followed these instructions but to no avail - still getting that error message. Any help please?

Did you put the font exe files directly into /etc/apt? It worked for me when I did that. And then, after reinstalling the package, those files were gone from the /etc/apt folder.

However, I had spent a few hours removing and reinstalling and completely removing and reinstalling the package, so maybe that had something to do with it... I also tried downloading and installing the .deb file manually from [http://packages.ubuntu.com]("http://packages.ubuntu.com/karmic/all/ttf-mscorefonts-installer/download"), but I don't think that helped (but maybe I'm wrong, maybe it did help somehow).

I'm not a Linux expert, but hopefully the solution I posted above will help at least a few people out there. I'm sorry if it can't help you.

---

### Post by panchito on 2009-10-28
Have a look into /etc/resolv.conf and put a "#" in front of your router's nameserver.

---

### Post by jonathank89 on 2009-11-06
I wrote up a fix for this! I don't see why my method wouldn't work for you.

Check out my post: [here]("http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

The basics of it is uninstall the ttf-mscorefonts-installer and then (optional) use the basic script i wrote to download and install the mscorefonts.

Hope it works for you guys.

---

### Post by tomcat025 on 2009-11-11
> **panchito said:**
> Have a look into /etc/resolv.conf and put a "#" in front of your router's nameserver.

Thank you for the tip above. Worked like a charm.

---

### Post by fitzdragon on 2009-11-20
> **jonathank89 said:**
> I wrote up a fix for this! I don't see why my method wouldn't work for you.

Check out my post: [here]("http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

The basics of it is uninstall the ttf-mscorefonts-installer and then (optional) use the basic script i wrote to download and install the mscorefonts.

Hope it works for you guys.

That worked really well , thanks a lot 

Antoin

---

### Post by PottyBert on 2009-12-12
I found that I had the same error, and it was caused by me manually installing the consolas.ttf font into /usr/share/fonts/truetype/ms-fonts/

I moved it out, deleted the ms-fonts dir and re-ran sudo apt-get -f install

It seems to have worked now

---

### Post by waiter on 2009-12-12
If you do not use proxies and have a conventional internet connection try this:

1. Open your /etc/wgetrc file as root (or with sudo).
2. Look for the line containing "#use_proxy = on"
3. Replace that with this: "use_proxy = off" and save
4. (Re)install ttf-mscorefonts-installer package.

It worked for me. :)

---

### Post by SOME1 on 2009-12-19
thanks to post #21 in [this page]("https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217") this is how I solved it; 

in terminal 

```
sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst
```

replace line 148 from this

```
if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then 
```

to this

```
if ! wget --continue --tries=1 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then
```

save and run in terminal 

```
sudo apt-get update
```

and 

```
sudo apt-get dist-upgrade
```

it worked for me.

---

### Post by nallen00 on 2009-12-31
> **SOME1 said:**
> ...it worked for me.
And me.  Thanks for posting this.  I was just about to do so myself ;)

---

### Post by nagaraj on 2010-01-03
i had the same problems in karmic. removing the installer solved. thanks

---

### Post by tazztone on 2010-01-04
i solved this problem by adding hosts to the etc/hosts file. to do so open a terminal and execute ```
sudo gedit /etc/hosts
```  add hosts so that it looks like this

```

127.0.0.1    localhost
127.0.1.1    tazz-laptop

216.34.181.59 downloads.sourceforge.net
212.219.56.167 kent.dl.sourceforge.net
213.203.218.122 mesh.dl.sourceforge.net
208.122.28.29 voxel.dl.sourceforge.net
212.219.56.167 sunet.dl.sourceforge.net
213.203.218.122 sunet.dl.sourceforge.net
208.122.28.29 sunet.dl.sourceforge.net
211.79.60.17 nchc.dl.sourceforge.net
130.59.138.21 switch.dl.sourceforge.net
194.95.236.6 dfn.dl.sourceforge.net
193.1.193.66 heanet.dl.sourceforge.net
150.65.7.130 jaist.dl.sourceforge.net
200.17.202.1 ufpr.dl.sourceforge.net
150.101.135.12 internode.dl.sourceforge.net
64.7.222.131 internap.dl.sourceforge.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

....
credits go to problem solving article at: [http://www.james-blogs.com/2009/11/20/fixing-the-ttf-mscorefonts-package-in-ubuntu-9-10/](http://www.james-blogs.com/2009/11/20/fixing-the-ttf-mscorefonts-package-in-ubuntu-9-10/)

---

### Post by mhtc on 2010-01-05
For those who got the font files into /etc/apt, as recommended in post #15, but could get no further, editing the ttf-mscorefonts-installer file by typing 

```

sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

```

into the Applications>Accessories>Terminal screen

and changing

```

LOCALCOPY=$RET

```

to

```

LOCALCOPY=/etc/apt

```

in the file, should work, if one reinstalls ttf-mscorefonts-installer using the Synaptic Package Manager under System>Administration.

---

### Post by Opie2010 on 2010-01-11
I checked and I am not running a proxy and there is no ttf-mscorefonts file in the archives of my apt folder, but I am still receiving. I'm trying to make the switch from Windows to Ubuntu but if packages can't be installed I have to go back. Any further help would be appreciated :)

double edit: I thought I found an answer but to no avail.

---

### Post by samurayx89 on 2010-01-26
I was having this problem and at first i didnt know why every app i installed gave me an error then i found about the ttf-mscorefont. I downloaded the deb tried reinstalling, removing and installing and that didnt work. Then i found this thread i tried the method from post 21 but it didnt work then i tried 15 here i found out that when i was downloading the fonts the [http://sourceforge.net/](http://sourceforge.net/) links that contains the exe files sent me to some mirrors which get me an error page (something about an infinite loop), i noticed that this had happened before and that i think the error with the deb and package manager is because they never get to download the files. So i tried downloading from the 15 post link again but this time selected to choose my own mirror and got one from japan and then i was able to download all the fonts. I tried installing again and got the same error but had a look at post 30 did what he said and installed perfectly.. thanks 15 and 30. 
So here is what i did and a link with all the fonts in it in [FONTS]("http://www.mediafire.com/?nk4emqgkzhw"),

This is some instruction based on post 15 and 30
(THis is assuming you have installed mscorefonts, i think if you remove it you wont be able to open the postinst file; just in case be sure is installed it, even tough it will only give you an incomplete installation)
1) Download fonts, open, select all and copy them (right click copy)
2) Open terminal and type
   gksudo nautilus 
3) In the new window 
   go to Filesystem then open /etc/apt and paste the fonts here    
4) Next in the terminal window type:
sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst
5) In this window replace the line "LOCALCOPY=$RET" to "LOCALCOPY=/etc/apt"
6) Close gedit and save what you did. Go to Synaptic Package Manager and reinstall ttf-mscorefonts-installer.

---

### Post by ghoststar on 2010-01-26
thanks to posts 20 & 30 I **FINALLY** got this installed properly... thanks alot guys.

---

### Post by seyed on 2010-02-16
Finally i found my problem origin...
Thanks government of USA!


> 
**403 Error – Forbidden**

 Your request is being denied as it appears to be coming from a location banned by our [Terms of Use]("http://p.sf.net/sourceforge/terms#ProhibitedPersons").

**Report Not Being From a Blocked Country**

                              If you are not from one of the countries banned from accessing this site, please submit us a Support Request including your IP address (78.38.xxx.xx) and country of origin.

:D :D :D
I'm from Islamic Republic of IRAN
This is not a good solution for USA government.

Not problem, i will find another way ;)

---

### Post by webdevelopment on 2010-02-18
is there a GUI that allows installation of windows true type TTF fonts?

---

### Post by patiepp on 2010-03-18
Guys if you are dual booting your system with Windows simply execute the following command in terminal
 sudo cp /media/C/Windows/Fonts/*.ttf /usr/share/fonts/truetype/msttcorefonts/ 

where, Replace "/media/C" by the path to your windows installation partition.
....and of-course mount the windows partition through file browser before.:D

---

### Post by sick-of-ttfmscorefonts on 2010-12-27
None of this helps

If I try to open synaptic package I get 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Nothing seems to work. When I try to install the package I get a scream with a notice from microsoft in terminal and there is an ok button I can not hit. It is like I can not finish the install.

I am about to format for the third time.

---

### Post by howefield on 2010-12-27
> **sick-of-ttfmscorefonts said:**
>  and there is an ok button I can not hit.

Try using the tab key to highlight the OK button and then press enter.

And open a new thread next time rather than appending to an old one. :)

---

### Post by sick-of-ttfmscorefonts on 2010-12-27
I deleted it in the vars/cache something folder and then sudo apt-get install... Tab and enter, oh and some arrow keys totally made it all work!!!!!!!

FIXED WOOOO

Screw that install. Thanks to you for helping, will start new topic next time.

---

### Post by virtualXTC on 2011-06-03
Had the same problem on a fresh kubuntu install with no firewall yet configed.  I couldn't even control-C out of the installer until i realize it was 2 processes I needed to quit and just started pushing control-C faster.

My work around was to control-c enough to allow the rest of the install to finish then
```
sudo dpkg --remove ttf-mscorefonts-installer
```

which was a bit easier than finding and removing each instance of it.  Hope this helps someone.  Sad that Ubuntu won't fix this bug, but is just another reason I'll be moving back to Debian soon.

---

### Post by murias002 on 2011-06-03
is easy to fix installing medibuntu repositories too, no more problems with windows compatiblity fonts, and other issues fixed.

---

### Post by LouisFlorian on 2013-04-26
I found the best solution here:
[http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html](http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html)

---

### Post by wildmanne39 on 2013-04-26
Thread closed. Please do not post in old threads.

---

