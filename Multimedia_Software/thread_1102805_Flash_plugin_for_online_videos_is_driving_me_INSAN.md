---
title: "Flash plugin for online videos is driving me INSANE! Can't get it to work right"
date: 2009-03-22
forum: Multimedia Software
---

### Post by VotaVader on 2009-03-22
Hi. I've been having this problem for about a week now, and I've tried everything I know (which isn't much) and a lot of stuff I've seen in forums about similar problems to fix it, but to no avail.

About 2 weeks ago I had a problem with the audio of online videos (youtube, etc...): there was none. I tried to fix it in all sorts of ways, but nothing was effective, so I decided to upgrade from Hardy to Intrepid in hopes that the bug would be mysteriously repaired. It was! And for a week, everything was fine.
Then one day, out of the blue, I started to get the "You don't have the latest Flash Player, get Flash Player 10 plugin, blah blah" message and videos wouldn't be displayed on any site. Of course I already had the latest plugin, javascript was enabled, and everything was supposedly working correctly... except it wasn't.

I tried uninstalling reinstalling everything from just the plugin, to all of firefox, plugins and ubuntu-restricted-extras (with purge), through Synaptic and by regular download of packages. After trying it in many different orders, I got the videos running again (with sound), but there's one other problem now. Every video stops somewhere in the middle, displaying that "loading" circle of white dots (even though the buffered stream is far ahead of the playing slider) and never starts again. It just stays there forever. Also, if I try to move the slider, the controls are rendered unresponsive.

I'm pretty desperate right now because I've been looking all over the net for an answer to this, and only seen similar situations, but mostly with the Flash Player 9 plugin. Please help me fix this!!

There are some strange messages that I've been getting through Synaptic that might be of consequence to this issue.
Every time I try to change the repository from which I download, I get something like this:
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
```
Or through the terminal:
```
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Hit http://archive.canonical.com intrepid Release
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Hit http://archive.canonical.com intrepid/partner Packages
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release              
Hit http://archive.canonical.com intrepid/partner Sources           
Hit http://archive.ubuntu.com intrepid-security Release
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/restricted Sources
Get:1 http://archive.ubuntu.com intrepid/main Packages [1256kB]
Hit http://archive.ubuntu.com intrepid/restricted Packages                     
Hit http://archive.ubuntu.com intrepid/multiverse Sources                      
Get:2 http://archive.ubuntu.com intrepid/universe Sources [1981kB]             
39% [1 Packages bzip2 4789248] [2 Sources 24403/1981kB 1%]          113kB/s 17s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com intrepid/main Packages                           
  Sub-process bzip2 returned an error code (2)
Get:3 http://archive.ubuntu.com intrepid/universe Packages [4542kB]            
Hit http://archive.ubuntu.com intrepid/multiverse Packages                     
Hit http://archive.ubuntu.com intrepid-updates/main Packages                   
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages             
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources              
Hit http://archive.ubuntu.com intrepid-updates/main Sources                    
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources              
Hit http://archive.ubuntu.com intrepid-updates/universe Sources                
Hit http://archive.ubuntu.com intrepid-updates/universe Packages               
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages             
Hit http://archive.ubuntu.com intrepid-security/main Packages                  
Hit http://archive.ubuntu.com intrepid-security/restricted Packages            
Hit http://archive.ubuntu.com intrepid-security/restricted Sources             
Hit http://archive.ubuntu.com intrepid-security/main Sources                   
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources             
Hit http://archive.ubuntu.com intrepid-security/universe Sources               
Hit http://archive.ubuntu.com intrepid-security/universe Packages              
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages            
Fetched 7779kB in 3min16s (39.6kB/s)                                           
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
This is what I get from the Main Server. Might the problem be that I'm installing corrupt packages? I get that idea because some of my failed installations of the plugin gave me results like this:
```
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87-2intrepid1_i386.deb
  Hash Sum mismatch
```
Or they were fetched, but had some other type of hash sum mismatch, and I got the message "flashplugin-nonfree was NOT installed". Note that the last installation I did worked fine and acknowledged no errors (flashplugin-nonfree is installed).

Some of the packages I've been playing around with are:
flashplugin-nonfree
adobe-flashplugin
firefox-3.0 (and dependencies)
ubuntu-restricted-extras (and dependencies)

Many thanks to anyone who can shed some light on this please!

Edit: Ok. I managed to fix the repository loading errors by replacing http with ftp on the sources.list file. Then I tried to reinstall the flashplugin-nonfree package and got the other hash sum mismatch I had talked about. There's barely any understandable info on this type of hash check to be gained from googling...

```
2009-03-22 19:22:39 (55.5 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3994294/3994294]

Download done.
sha256sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.
```

---

### Post by gandaran on 2009-03-22
> Download done.
sha256sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.
this error is due to the flash package update, you must first retrieve the new apt/synaptic package list before installing flash, to fix it you must first **completely** remove the broken flashplugin-nonfree package, use synaptic for this or the purge command then update by running **sudo apt-get update** or by clicking the reload button in synaptic package manager, now you can reinstall the updated flashplugin-nonfree package.
theres no need to have two flash packages installed, adobe-flashplugin and flashplugin-nonfree install exactly the same adobe flash plugin, there isn't any deference in any of them except they install flash in deferent plugin directories, two flash plugins installed may complicate things for firefox and make sure you don't have any open source flash installed (gnash and swfdec plugin) too.

---

### Post by VotaVader on 2009-03-22
> **gandaran said:**
> this error is due to the flash package update, you must first retrieve the new apt/synaptic package list before installing flash, to fix it you must first **completely** remove the broken flashplugin-nonfree package, use synaptic for this or the purge command then update by running **sudo apt-get update** or by clicking the reload button in synaptic package manager, now you can reinstall the updated flashplugin-nonfree package.
theres no need to have two flash packages installed, adobe-flashplugin and flashplugin-nonfree install exactly the same adobe flash plugin, there isn't any deference in any of them except they install flash in deferent plugin directories, two flash plugins installed may complicate things for firefox and make sure you don't have any open source flash installed (gnash and swfdec plugin) too.

I've tried updating the package list a thousand times, and with many different servers, and removing completely then reinstalling, but I keep getting the same message.
Could it be that I somehow messed up the update from hardy to intrepid? Cause I remember that when I did it, each time I was prompted, I chose to keep my existing GRUB menu, but that's the only thing I did outside the default...

---

### Post by gandaran on 2009-03-22
> **VotaVader said:**
> I've tried updating the package list a thousand times, and with many different servers, and removing completely then reinstalling, but I keep getting the same message.
Could it be that I somehow messed up the update from hardy to intrepid? Cause I remember that when I did it, each time I was prompted, I chose to keep my existing GRUB menu, but that's the only thing I did outside the default...
you must remove completely first, not just remove or you'll land up installing the same broken package, then update and only then install, if you don't follow these steps you'll never get it installed, and check if the security and recommended update channels are enabled.

---

### Post by ami_nakata on 2009-03-22
( Oh!  I just saw that VotaVader is still having problems.  Don't meant to be rude by following up on his/your topic this way, but the problem I've been having seems similar-enough that it might just be relevant?  Apologies if not, along with much   commiseration.  I am curious, though, VotaVader, as to whether you could "trash Flash" in favor of Gnash?  And also, whether your Firefox error console shows any XPCOM errors, as mine does?  And if so, whether executing run-mozilla.sh reveals any missing dependencies on your machine?  Apologies in advance if this isn't helpful: as I wrote below, you guys - VotaVader and gandaran - are much more experienced than I am...

That said, I suppose you did remove the hidden directories for Flash under your HOME directory? My recollection is that there were two on my machine, one under .adobe and one (I think) under .macromedia(?).  If it helps at all, here's what I remember of how I was able to lose Flash on Hardy, although I don't know if the same version and/or problems would come back to haunt me were I to try to reinstall it.   

I used Synaptic to mark both flashplugin-nonfree and adobe-flashplugin for **"complete** removal".  Then I executed

sudo apt-get remove flashplugin-nonfree
sudo apt-get remove adobe-flashplugin 

... or maybe it was "autoremove" rather than remove; probably was, but I forget. But according to what I saw on the web, > The autoremove removes all unused dependencies. After that remove the residual config in Synaptic. Also use GTKOrphan to clean up your Ubuntu. I also recommend the following commands to clen your Ubuntu installation.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremoveI didn't know how to use GTKOrphan, so I didn't, although maybe you will.  I did use the last three commands, though.

Also, if this isn't relevant enough, or helpfully-related at all, please ignore it and focus on VotaVader's problem, since it's his thread, and I'll re-post a re-edited version in (say) absolute beginners.  Or maybe I'll just go with that Amish thing - see following - after all.  The longer I spend on this, the more attractive that begins to look anyway!  

Thank you. - Ami )

ORIGINAL/INTENDED POST FOLLOWS BELOW:

Sounds like my own experience, except I'm much less experienced than you guys ... I HATE Flash!  I bet Adobe's executives torment puppies for fun when they're not coming up with new ways for their programmers to torment users!  Can't say I'm a whole lot happier with Mozilla/Firefox at present, either.

Anyway, if the original poster got his problem sorted out (?) - don't want to supersede his thread, if not - I could really really really use some help, too, please.

After an ordeal similar to what he described, I finally (!) succeeded in completely uninstalling Flash.  I gave up on Flash altogether, and installed gnash 0.8.2 via synaptic.  Others have said 0.8.2 gnash worked for them with Firefox on (e.g.) YouTube, but it doesn't work for me.  ( The developers of gnash have released 0.8.5, btw, although I don't know how to install that since it's not presently available through Synaptic's current configuration on my Hardy Heron machine. )

I think that might be because Firefox has some missing dependencies, which I discovered immediately after it was automatically "upgraded" to ver 3.0.7 via the ubuntu "update notification" thing a couple of days ago.  ( Everything had been working fine before the update, even Flash. Then after the update I could still watch YouTube videos, but not those on fancast.com, which I'd been able to do right before the update. )

So I looked at the Firefox error console - this is before I uninstalled Flash, or even tinkered with the sytem at all - but after the update.  This is what I saw,

```

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.7/components/pyabout.py
Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so

Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Source File: http://www.fancast.com/static-19052/css/base.css
Line: 28

Warning: Unknown property 'resize'.  Declaration dropped.
Source File: http://www.fancast.com/static-19052/css/base.css
Line: 41
```along with a bunch of similar errors related to base.css.  I understood the .css errors to be relatively unimportant (right?), but found that that the XPCOM errors might indicate missing dependencies.  I based that on info from these two pages, btw:

[http://forums.mozillazine.org/viewtopic.php?f=19&t=787565](http://forums.mozillazine.org/viewtopic.php?f=19&t=787565)
[https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration#Linux-specific_hints](https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration#Linux-specific_hints)
  
That second link says to execute "run-mozilla.sh", and that there "should be no 'not found' entries and no undefined symbols" in the output that results.

Unfortunately, I **did** get "not found" and "undefined symbols" as output:

```
me@mypc:~$ /usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so
    linux-gate.so.1 =>  (0xb7f46000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f1d000)
    libxpcom.so => not found
    libxul.so => not found
    libplds4.so.0d => /usr/lib/libplds4.so.0d (0xb7f19000)
    libplc4.so.0d => /usr/lib/libplc4.so.0d (0xb7f15000)
    libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0xb7ee2000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ede000)
    libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0xb7da8000)
    libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7da4000)
    libpyxpcom.so => not found
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7cb1000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c8c000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7c80000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b31000)
    /lib/ld-linux.so.2 (0xb7f47000)
undefined symbol: _ZN14Py_nsISupports21PyObjectFromInterfaceEP11nsISupportsRK4nsIDii    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z16PyXPCOM_LogErrorPKcz    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _ZN14Py_nsISupports21InterfaceFromPyObjectEP7_objectRK4nsIDPP11nsISupportsii    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z24PyXPCOM_MakePendingCallsv    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z31PyXPCOM_EnsurePythonEnvironmentv    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z34PyXPCOM_SetCOMErrorFromPyExceptionv    (/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
me@mypc:~$ 

```In the first of the two links above the immediately-preceding code box, the poster there says: 

> Annoyingly enough (but also a bit of a relief), all I had to do was move the LDFLAGS to the end of my g++ command to fix a raft of unresolved symbols. The most time consuming problems often have the simplest solutions...I wish I could copy his solution, but I barely understand what he means.  I don't have a clue as to how I might go about re-compiling something to resolve the missing dependencies that Firefox reported, the XPCOM problems.

Does that mean I just have to wait for a "fix for the fix", have to wait for some automatic update to Hardy Heron 8.04, or will have to upgrade to 8.10 or something?  

I'd hate to think it'd mean I have to uninstall Firefox; a look-around on the web and here in the forums makes it look worse than trying to get Flash uninstalled, if anything could be. Here's another nightmare of an example, in a thread entitled "I have uninstalled Firefox ... yet it is still there."

[http://ubuntuforums.org/archive/index.php/t-735122.html](http://ubuntuforums.org/archive/index.php/t-735122.html)

I think they make it hard to uninstall on purpose, it's hard to imagine that it could be so difficult just by accident! 

I'd really appreciate help with this.  I was going through a free online course from MIT on the web before the upgrade broke my video playback, and I'd like to get back to it before I forget the little I've learned so far.  Besides, if I have to spend another couple of days on this I think I'll just have to give up on technology and join the Amish! 

thanks, 

- Ami

---

### Post by ami_nakata on 2009-03-22
Did I actualy ask if "you could trash Flash in favor of Gnash?"  Yikes!!!  Way, way too long on the computer trying to resolve this.  Sorry. Going outside now. 

- Ami

---

### Post by VotaVader on 2009-03-23
Ok. I tried everything you guys suggested (except for the GTKOrphan, which I don't know how to use, and the Gnash comment... which I'll subtly ignore for now). I'm not really proficient with Linux, as I just started using it a couple of months ago, so I'm not really that "experienced" Ami XD.
Well anyway. Here's what I got:
For the run-mozilla thing I got mostly the same results as Ami:
```
pedro@pedro-laptop:/var/cache/apt/archives$ /usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so
	linux-gate.so.1 =>  (0xb7fac000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f7a000)
	libxpcom.so => not found
	libxul.so => not found
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0xb7f75000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0xb7f70000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0xb7f3a000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f36000)
	libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0xb7df9000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7df5000)
	libpyxpcom.so => not found
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7d07000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ce1000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7cd1000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b73000)
	/lib/ld-linux.so.2 (0xb7fad000)
undefined symbol: _ZN14Py_nsISupports21PyObjectFromInterfaceEP11nsISupportsRK4nsIDii	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z16PyXPCOM_LogErrorPKcz	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _ZN14Py_nsISupports21InterfaceFromPyObjectEP7_objectRK4nsIDPP11nsISupportsii	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z24PyXPCOM_MakePendingCallsv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z31PyXPCOM_EnsurePythonEnvironmentv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z34PyXPCOM_SetCOMErrorFromPyExceptionv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
```

The flashplugin-nonfree package keeps giving me a sha256sum mismatch. And yes, I 'completely removed' everything through both Synaptic and terminal (--purge) and cleaned everything of flash, then updated the package list and tried to install. I did this with many different servers and repositories, all with the same result.
I finally got it "working" again (it shows video, but it still stops somewhere along and becomes unresponsive) by removing everything (again) and installing the adobe-flashplugin package and the konqueror-nsplugins ttf-xfree86-nonfree xfs package. The last one gave me a hashsum mismatch the first time, but when I ran it again with --fix-missing, it installed correctly (supposedly).
Now I'm stuck again with videos that stop to "load" in the middle, and never start again... damn this.
 
The Firefox error console (which I had not thought of reviewing) gave me a truckload of warnings when I tried to play a video on Youtube (after getting it working again), but no errors. The warnings were of the type:
```
Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Source File: http://s.ytimg.com/yt/cssbin/www-core-vfl83815.css
Line: 1

Warning: Expected declaration but found '*'.  Skipped to next declaration.
Source File: http://s.ytimg.com/yt/cssbin/www-core-vfl83815.css
Line: 1

Warning: Error in parsing value for property 'filter'.  Declaration dropped.
Source File: http://s.ytimg.com/yt/cssbin/www-core-vfl83815.css
Line: 1

etc...
```

but I got no XPCOM errors, and judging by the amount of warnings that crop up in the console (including from [http://ubuntuforums.org/clientscript/vbulletin_css/](http://ubuntuforums.org/clientscript/vbulletin_css/) while I'm writing this reply) I assume they are normal, or at least not so important. Maybe someone with a healthy flash plugin could confirm if they also get warnings on the error console when watching a video online.

Any other takers to try and solve this (or should I say these now) mysteries?

---

### Post by ami_nakata on 2009-03-23
Hi VotaVader -  

I get all the .css errors too, btw, and agree that they're probably not anything to worry about.  Perhaps I should have mentioned, though, that the XPCOM errors only came up intermittently for me; I cleared the Firefox error log repeatedly, to start with a "fresh slate", and they didn't appear with any real predictability that I could determine.

That said, after about 20 hours investigating this and learning about how Mozilla apps (including Firefox) work internally, I'm nearly certain that the three missing shared object (.so) files, also called "shared libraries", and the six undefined symbols, 

```

*( reformatted manually, for clarity )*

linux-gate.so.1            => (0xb7f46000)
libpthread.so.0            => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f1d000)
**libxpcom.so              => not found** 
**libxul.so                    => not found**
libplds4.so.0d              => /usr/lib/libplds4.so.0d (0xb7f19000)
libplc4.so.0d               => /usr/lib/libplc4.so.0d (0xb7f15000)
libnspr4.so.0d             => /usr/lib/libnspr4.so.0d (0xb7ee2000)
libdl.so.2                    => /lib/tls/i686/cmov/libdl.so.2 (0xb7ede000)
libpython2.5.so.1.0     => /usr/lib/libpython2.5.so.1.0 (0xb7da8000)
libutil.so.1                   => /lib/tls/i686/cmov/libutil.so.1 (0xb7da4000)
**libpyxpcom.so         => not found**
libstdc++.so.6             => /usr/lib/libstdc++.so.6 (0xb7cb1000)
libm.so.6                     => /lib/tls/i686/cmov/libm.so.6 (0xb7c8c000)
libgcc_s.so.1                => /lib/libgcc_s.so.1 (0xb7c80000)
libc.so.6                       => /lib/tls/i686/cmov/libc.so.6 (0xb7b31000)
/lib/ld-linux.so.2 (0xb7f47000)

[I]( Six undefined symbols were also reported, all associated 
with /usr/lib/**xulrunner**-1.9.0.7/components/libpyloader.so )
[/I] 
 _ZN14Py_nsISupports21PyObjectFromInterfaceEP11nsISupportsRK4nsIDii    
 _Z16PyXPCOM_LogErrorPKcz
 _ZN14Py_nsISupports21InterfaceFromPyObjectEP7_objectRK4nsIDPP11nsISupportsii
 _Z24PyXPCOM_MakePendingCallsv
 _Z31PyXPCOM_EnsurePythonEnvironmentv
 _Z34PyXPCOM_SetCOMErrorFromPyExceptionv
```that we're both seeing on executing run-mozilla.sh are actually a *very* big deal.

I'm toward the end of creating a document that I suspect might need to become a launchpad bug report re the Firefox 3.0.7 upgrade that was just released to Ubuntu users as an official update. A real programmer could probably express the problem and document its likely solution in a paragraph or two, but it'll probably take me 2 - 3 more hours to finish.  Here's an excerpt for the moment, though, that documents the current state of my understanding about what these libraries are for, what they do:

> For any non-ubergeeks - like myself - who may be trying to follow this, some definitions might be helpful:  Files with the ".so" extension are "shared objects", also called "shared libraries", and ".py" files are Python scripts.  I also see from the web that "XPCOM" means "Cross Platform Component Object Model", and refers to a framework for developing cross platform software that can be written in C, C++, or JavaScript with extensions for Perl and Python.  Also, I learned from Wikipedia that XUL is an XML-based user-interface markup language developed by the Mozilla project which operates in Mozilla cross-platform applications such as Firefox and Flock, and that **XULRunner is a runtime environment, also ****developed by Mozilla to provide a common back-end for XUL applications, of which ****Firefox is one**. Finally, a file that's integral to the problem I'm documenting here is named "libpyxpcom.so". As will be seen in the output from run-mozilla.sh, several lines below, that's one of three files/libraries/shared-objects that can't be found by libpyloader.so.  For that reason I want to quote the following from Wikipedia: "PyXPCOM allows for communication between Python and XPCOM, such that a Python application can access XPCOM objects, and XPCOM can access any Python class that implements an XPCOM interface." I'm getting ahead of myself to say this just now, but **I'd guess that if libpyxpcom.so is "missing in action" then all the Mozilla/Firefox python code that needs to communicate with XPCOM components won't be able to do so.**Basically, XPCOM and these libraries were created by the Mozilla Foundation as the application framework Firefox is built upon; they're absolutely foundational.  I'm pretty sure that if some of the libraries aren't accessible then Firefox just isn't going to work correctly at all.

I'm the more convinced of this because (among the many other sources on the web I found to support that supposition) I found a launchpad bug from about 9 months ago that shows the same thing happening with a previous release.  The guys discussing that bug included the people who put the Ubuntu package for Firefox updates together; the document I'm almost done with is intended primarily for them, although I'll at least provide a link to it in this thread, once I'm done with it.

At this point I do think a fairly straightforward workaround will be possible, but I'm *extremely* reluctant to suggest one right now from among the multiple possibilities suggested by the stuff I've seen as I've been researching this. I don't want anyone to make anything worse based on a faulty or incompletely-researched recommendation from me.   I'd caution against trying it - especially since I'm very much learning as I go in all this, and am no techno-geek at all, but if you absolutely can't wait I will mention that one possiblity that was suggested by what I saw would be to remove Firefox - although that can be a huge pain, a multi-day ordeal, too, as other posters here have documented - and install the 3.0.7 download directly from Mozilla, instead of applying the Ubuntu-specific package.  Might end up losing bookmarks, add-ons, configuration details that way, though, or worse.

Of course, I'm not seeing the checksum errors you report re flash ... haven't checked that out myself, at all.  So maybe what you're seeing really is due primarily to flash, but I'd be very surprised if the missing XPCOM library dependencies that Firefox needs to work properly weren't (at least) a sigificant contributing factor as well.

cheers, 

- Ami

---

### Post by ami_nakata on 2009-03-28
It's much later than I expected it would be on this, but I've posted a request on "launchpad answers" asking for help determining if the errors I reported above constitute an actual bug, rather than merely a user-specific configuration problem.  See [https://answers.launchpad.net/ubuntu/+question/65595](https://answers.launchpad.net/ubuntu/+question/65595) for additional documentation of the problem and eventually, as I hope, an answer on that. 

I don't know to what extent, if at all, any forthcoming answer via "launchpad answers" might apply to the problem VotaVader documented, however.

cheers,

- Ami

---

### Post by VotaVader on 2009-03-28
I... DON'T... BELIEVE IT...
I actually did a fresh install of Ubuntu the other day, and guess what... the problem persisted. So I got really suspicious. The thing is, the problem was the stupidest thing ever: THE CULPRIT WAS THE NETWORK CONNECTION!

I tried to watch a video while connected to the network at my university, and it worked like a charm... back at my house, same problem as before. I still find it strange that it failed from one day to the next, and that the flash plugin got corrupt (message that I didn't have it installed). Also the recurring hashsum mismatch is strange. I still can't properly install flashplugin-nonfree successfully, and have to use adobe-flashplugin instead (although they're supposedly the same, it's still weird).
I have a hunch that my network card and/or it's driver are failing or not configured properly...

I suppose this isn't the case with your problem Ami, right?

---

### Post by gandaran on 2009-03-28
> **VotaVader said:**
> I... DON'T... BELIEVE IT...
I actually did a fresh install of Ubuntu the other day, and guess what... the problem persisted. So I got really suspicious. The thing is, the problem was the stupidest thing ever: THE CULPRIT WAS THE NETWORK CONNECTION!

I tried to watch a video while connected to the network at my university, and it worked like a charm... back at my house, same problem as before. I still find it strange that it failed from one day to the next, and that the flash plugin got corrupt (message that I didn't have it installed). Also the recurring hashsum mismatch is strange. I still can't properly install flashplugin-nonfree successfully, and have to use adobe-flashplugin instead (although they're supposedly the same, it's still weird).
I have a hunch that my network card and/or it's driver are failing or not configured properly...

I suppose this isn't the case with your problem Ami, right?
two questions; 
did you install all updates after doing the fresh ubuntu install? 
which ubuntu version, 32-bits or 64-bits?

---

### Post by VotaVader on 2009-03-28
> **gandaran said:**
> two questions; 
did you install all updates after doing the fresh ubuntu install? 
which ubuntu version, 32-bits or 64-bits?

32 bits. Yes, I did all the updates, although I still get errors when I load repositories, so maybe I'm missing some update packages that weren't fetched properly so aren't recognized by the updater...

---

### Post by aaahotdog on 2009-03-28
I couldn't get any flash to work properly.   Same thing, it would always ask me to download flash plugin.   I am using Firefox 3 in Ubuntu 8.04.   I have loaded/unloaded several times.   The problem in my case was resolved by selecting edit/preferences in the browser and linking the asf video to gnash in the etc/bin folder.  Now youtube and pandora and rhapsody magically work.   Hope this helps.

---

### Post by ami_nakata on 2009-03-29
@VotaVader: I'm really glad to hear you got it working! What a huge pain to have had to go through!  I'll definitely look at my own network setup, but I think my system might be too messed up to go forward with. I'm considering trying to reinstall,  (yikes!) as you did, before proceding any further. To note just one problem, for example, both Synaptic and dpkg showed that the last Flash installation I attempted had finished properly, and Flash was installed. But now I can't get Firefox to recognize it as present when I look in the Add-ons screen. I think I deleted some directories I shouldn't have at one point, in my frustration, to try to make sure I'd completely uninstalled Flash and Firefox before attempting a fresh install of those two rascals.

> aaahotdog wrote:

*The problem in my case was resolved by selecting edit/preferences in the browser and linking the asf video to gnash in the **etc/bin** folder.  Now youtube and pandora and rhapsody magically work.*  @aaahotdog:  Did you mean the **/usr/bin** folder?  I just installed (and then uninstalled) gnash 0.8.2, and found the executable in /usr/bin.

 But thanks, aaahotdog, for the comment. I'm really very pleased to hear that gnash actually works; what version are you using?  I'd like to stop using Flash altogether, too: [http://ubuntuforums.org/showthread.php?p=6966254](http://ubuntuforums.org/showthread.php?p=6966254) , ( to which I got no reply :( at all ).  

I'm pretty sure I tried the seriously outdated 0.8.2 version of gnash at one point, the default one available under Hardy's synaptic, but I couldn't get it to work, and I couldn't figure out how to install the 0.8.5 version from the web, nor could I successfully employ the 0.8.4 ubuntu-specific repository I found for Hardy at [http://www.getgnash.org/packages/releases/ubuntu/hardy/](http://www.getgnash.org/packages/releases/ubuntu/hardy/).  Synaptic downloaded the packages from that repository ( if that's the right word ), but when it tried to install them it said there was an error in their index.  Possibly my "apt" line was faulty.  I wasn't exactly sure of the syntax; I think I used: 

```
deb http://www.getgnash.org/packages/releases/ubuntu/hardy/ hardy universe
```That suffix, "hardy universe" was probably at fault, I suppose.

I wonder, aaahotdog, whether you'd mind trying to view a streaming video on [http://www.fancast.com]("http://www.fancast.com/") using your gnash-enabled browser?  That's always been my "acid test" to see whether a video plugin works; it's the most fussy streaming video site I've found, and I'd be curious to know. ( I can watch youtube video on when I've booted from my Vista partition, for example, but not Fancast. )

  Even if I could get a more recent gnash version installed on my sytem, I still couldn't get Firefox to use it for the "asf video" type you mention. My system is so messed up at this point that my current Firefox 3.0.8 install shows only six mime types registered in under Edit > Preferences > Applications, viz:  mailto; Podcast; Software package; Video Podcast; webcal; and Web Feed.  I haven't been able to figure out how to get the rest of them back, e.g. the "asf video" type that you mention. I suspect that might have something to do with the fact that the "Default Plugin" is showed as not enabled via about : plugins, but as properly enabled via Tools > Add-ons > Plugins. It could be one of a dozen different things, though, as messed up as my system is currently. 

But here's a *simple* question, to finish with: can anyone let me in on how to get the "quotation box" that includes the legend (e.g.) "Originally Posted by gandaran"?  I haven't been able to find info about that.

cheers, 

- Ami

---

### Post by VotaVader on 2009-03-29
> **aaahotdog said:**
> I couldn't get any flash to work properly.   Same thing, it would always ask me to download flash plugin.   I am using Firefox 3 in Ubuntu 8.04.   I have loaded/unloaded several times.   The problem in my case was resolved by selecting edit/preferences in the browser and linking the asf video to gnash in the etc/bin folder.  Now youtube and pandora and rhapsody magically work.   Hope this helps.

Hey! That actually worked!!
I had ASF video linked to Windows Media Player plug-in 10, I changed it to the Movie Player (default), and now it works at home too! It still stops sometimes and does the "loading" thing sometimes, but I just have to reload the page. Also, the framerate seems to be better.
I also tried linking the ASF videos to vlc media player (/usr/bin/vlc) and it works perfectly, albeit with some diminished framrates (I don't actually know if it's the framerate, but it looks a bit more clunky). I haven't tried it with gnash, because I have already installed too much crap during this whole ordeal, but anyone else is welcome to try it!

Ami, to quote from another person and cite their name and such you can either click on the "quote" button next to the post you want to quote or you can start the quote section with ```
[QUOTE=username;#of_the_post] 
```
To get the number of the post, just hover your mouse over the post while replying (I'm pretty sure there's another way, but that's the one I know)

---

