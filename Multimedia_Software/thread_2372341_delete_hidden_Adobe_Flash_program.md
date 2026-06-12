---
title: "delete hidden Adobe Flash program"
date: 2017-09-23
forum: Multimedia Software
---

### Post by Nick Levinson on 2017-09-23
I want Adobe Flash gone, because it's a security risk. A recent update to my Linux installation said it was adding Flash or updating it. But I can't find it. I assume it's embedded in something else. How do I find it or verify its absence?

---

### Post by &amp;KyT$0P# on 2017-09-24
> **Nick Levinson said:**
> A recent update to my Linux installation said it was adding Flash or updating it. 
What is the exact message you got?

> But I can't find it. ... How do I find it or verify its absence?
What have you tried so far?

---

### Post by Nick Levinson on 2017-09-25
I don't remember the exact message and I don't expect it to reappear if the installation is already finished. That's why I gave only the gist of it.

When I search my laptop for apps with the search term "Flash" (without quote marks), all that comes up is Claws, which I haven't set up and don't want to (maybe later). Firefox v55.0.2 (64-bit) seems to have it but it's not listed in the hamburger menu > Add-ons, which lists only OpenH264 Video Codec, so I can't refuse to activate Flash. Mozilla's help articles talk about other subjects that are kind of close (like uninstalling Firefox), so I guess Mozilla's decision is to prevent deactivation or uninstallation of Flash itself. I don't know if Flash is embedded in some other program. I did some Googling without much result.

---

### Post by &amp;KyT$0P# on 2017-09-25
Please post the output (if any) from running this command in Terminal -
```
dpkg-query -W | grep -i flash
```

---

### Post by Nick Levinson on 2017-09-28
No output came, whether I added sudo to the beginning or not, even though with sudo it asked me for my password. When I ran

sudo dpkg-query -W flash

I got:

dpkg-query: no packages found matching flash

Then I ran

sudo dpkg-query -W *flash*

which got:

adobe-flashplugin
gnome-session-flashback

Googling tells me that gnome-session-flashback is irrelevant to this effort.

I ran

sudo dpkg -S adobe-flashplugin

which got:

dpkg-query: no path found matching pattern *adobe-flashplugin*

I ran

sudo dpkg -S *flash*

which got a list of roughly 410 items, which I skimmed visually, finding nothing that seemed likely. Sampling the beginning of the list, about two thirds have flash as a whole word, according to Terminal's search dialog, and most of those are in file names. So maybe it's there among 250 or so items and my eyeballs missed it.

I guess that if Flash is embedded in another program then a totally different name is possible, as is that it's not a separate file when installed on a hard drive. I'm not even sure how to Google what such a package might be called if not flash, though I tried. A superficial search of Adobe.com didn't get the answer; they say what to get to install Flash but I suspect they won't want to help with removing it. A search for "uninstall Flash" (without quote marks) in adobe.com wasn't helpful.

---

### Post by kurt18947 on 2017-09-28
Do you have Synaptic installed? That is part of my default install and I've used it to install, delete and reinstall various packages. I'm sure I don't use Synaptic to its potential but I prefer it as a package manager to Software Center.

---

### Post by &amp;KyT$0P# on 2017-09-28
> **Nick Levinson said:**
> No output came, whether I added sudo to the beginning or not,
So you don't have any Flash package installed.

> Then I ran

sudo dpkg-query -W *flash*

which got:

adobe-flashplugin
gnome-session-flashback

If you give it a pattern, it will list packages that are not installed.

> I guess that if Flash is e
You could also try to ferret out Flash this way -
```
sudo find / -iname '*flash*' -ls 2>&1 | tee ~/find-flash.txt
```
Look at the contents of the generated [FONT=Courier New]find-flash.txt[/FONT] file.

Not every result is necessarily Adobe Flash.  Please post here before taking any action.

---

### Post by Nick Levinson on 2017-10-03
That got this:

[sudo] password for . . .: -iname: command not found

(brackets so in original & ellipsis for my account name)

The Enter key got this:

[2]+  Stopped . . .

(ellipsis for copied command line)

Removing the first pipe allowed password entry, recognition of -iname, and generation of the *.txt file, which had the following entries (I edited the account name out and deleted an entry for a file I created by error), which I guess show that Firefox has Flash and nothing else on my machine does:

  ```
6427437      8 -rw-rw-r--   1 [useraccountname]     [useraccountname]            0 Oct  3 04:19 ./find-flash.txt
  6951677     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flash-simple.sbstore
  6951658     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashsubdoc-digest256.sbstore
  6951660     92 -rw-rw-r--   1 [useraccountname]     [useraccountname]        82780 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/block-flashsubdoc-digest256.sbstore
  6951664     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          556 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashinfobar-digest256.sbstore
  6951665     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/block-flash-digest256.pset
  6951679     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flashsubdoc-simple.sbstore
  6951675     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/allow-flashallow-digest256.pset
  6951676     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flashallow-simple.pset
  6951671     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flash-simple.sbstore
  6951691     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flashsubdoc-simple.sbstore
  6951657     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flashallow-simple.sbstore
  6951684     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flash-simple.pset
  6951686     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          268 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flash-digest256.sbstore
  6951688     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/test-flashsubdoc-simple.pset
  6951689     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/allow-flashallow-digest256.sbstore
  6951690     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashsubdoc-digest256.pset
  6951680     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flashallow-simple.sbstore
  6951692     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flashsubdoc-simple.pset
  6951696     16 -rw-rw-r--   1 [useraccountname]     [useraccountname]         7648 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/block-flash-digest256.sbstore
  6951697     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashinfobar-digest256.pset
  6951698     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/block-flashsubdoc-digest256.pset
  6951699     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]          232 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashallow-digest256.sbstore
  6951701     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flash-simple.pset
  6951702     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/testexcept-flashallow-simple.pset
  6951703     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flash-digest256.pset
  6951706     12 -rw-rw-r--   1 [useraccountname]     [useraccountname]           16 Oct  3 04:01 ./.cache/mozilla/firefox/tccfw4ph.default/safebrowsing/except-flashallow-digest256.pset
```

A risk that occurs to me is that if Firefox no longer allows removing Flash from inside it and I try to do that then I'll break Firefox, which would give me an operational dilemma, functionality vs. security.

On another laptop, Firefox had this banner: "Firefox has prevented the outdated plugin 'Adobe Flash' from running on [URL]" (FF v47.0 on PCLinuxOS (2016)). That Firefox lists Flash among the browser's plugins, whereas the newer Firefox on my Ubuntu platform, which runs Flash, does not list it.

Listing packages that are not installed is puzzling, because either I have uninstalled packages lying on my machine (if so, it's not deliberately by me) or it lists everything that could be downloaded, which I assume would be a massive list, in which case listing just two makes that explanation very unlikely. To test whether it's listing what's not even on my machine, I disabled networking and ran the command again, and still got just the two items; thus showing that what the command line produced was only what was on my machine.

Synaptic (@kurt18947): The only thing I have like that is an image (synaptic_synaptic.png). I tend to stay with what is offered with or through a distro, in case there are software conflicts otherwise, so I likely won't install Synaptic, although it appears that quite a number of people use it.

---

### Post by &amp;KyT$0P# on 2017-10-03
[s]You do not have Adobe Flash at all.[/s]  The Firefox-related files you found are just safebrowsing lists.

* Just noticed that your output is **not** from running [FONT=Courier New]find[/FONT] across the entire filesystem.  Somehow you morphed the command to only search your home directory.  So we actually don't know yet whether you have Flash somewhere or not.

Do you not use [FONT=Courier New]bash[/FONT] or [FONT=Courier New]ksh[/FONT] as your shell?  The command as I typed it should work as-is with either of those.

---

### Post by wildmanne39 on 2017-10-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Nick Levinson on 2017-10-07
My fault. I misread the first slash as a pipe, thus the failure of the command line and the failure to capture data for the whole filesystem. I reran the command line, then edited the resulting file to replace my main nonroot account name and user group name including in URLs (I set up another nonroot account but it was not identified in this file).

That content is now at <https://paste.ubuntu.com/25696194/>.

The first line says "Permission denied". I did nothing in response, it appeared only for seconds (if that much) before the next line appeared and they scrolled out of sight, and the output continued by itself in bursts till it was ready for my next CLI input, which was "exit".

On bash or ksh, the terminal app says I'm using bash, so I assume I was at all times, since I don't change it intentionally.

---

### Post by &amp;KyT$0P# on 2017-10-07
You do not have Adobe Flash on your computer.  But I think you do have one Flash-related file -
```
/usr/share/app-install/desktop/flashplugin-installer.desktop
```
Quick search indicates it's from the package [app-install-data]("https://packages.ubuntu.com/xenial/app-install-data").

---

### Post by vasa1 on 2017-10-07
> **halogen2 said:**
> You do not have Adobe Flash on your computer.  But I think you do have one Flash-related file -
```
/usr/share/app-install/desktop/flashplugin-installer.desktop
```
Quick search indicates it's from the package [app-install-data]("https://packages.ubuntu.com/xenial/app-install-data").
@halogen2, I don't have *app-install-data* (on Kubuntu 16.04). I looked at its *depends*, *reverse depends* and *apt show* but didn't see any flash-related files. And I don't have */usr/share/app-install/*. Maybe that explains why I don't see it.

---

### Post by &amp;KyT$0P# on 2017-10-08
vasa1, I don't have that package installed either.  But if you download and extract the package, you can see that one file is definitely Flash related -
```
$ cat usr/share/app-install/desktop/flashplugin-installer.desktop
[Desktop Entry]
Comment=Installer for the Adobe Flash plugin for Mozilla
Name=Adobe Flash plugin
Icon=adobeflashplugin
Encoding=UTF-8
Terminal=false
Type=Application
Categories=GNOME;Application;Internet;
X-AppInstall-Package=flashplugin-installer
X-AppInstall-Popcon=1295
X-AppInstall-Section=multiverse
X-AppInstall-Architectures=i386,amd64
X-Ubuntu-Gettext-Domain=app-install-data

```

---

### Post by vasa1 on 2017-10-08
Understood! I think I had that sort of folder in Lubuntu and it listed a vast number of .desktop files whether the user has ever installed them or not.```
X-AppInstall-Popcon=1295
```isn't present in "normal" .desktop files.

---

### Post by Nick Levinson on 2017-10-09
This is interesting: In </usr/share/app-install/desktop/>, I don't see flashplugin-installer.desktop with my eyes, but Search for Files lists it in a search only for "flashplugin" (without quote marks) and a terminal lists it, as does the paste.ubuntu.com list, as you noticed. Then I eyeballed the folder again and found "Adobe Flash plugin" (without quote marks); according to Properties, the Comment is "Installer for the Adobe Flash plugin for Mozilla" but Properties does not list the name found in the terminal or search. Both purported files are the same size and have the same last-modified date-time and seem to be the same file, just named differently according to where you look, and therefore alphabetized at different locations.

Mozilla says we do have Flash in Firefox. [https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems) offered a Flash test page; I tried it and did not get the negative statement Mozilla described for not having Flash. [https://blog.mozilla.org/futurereleases/2015/10/08/npapi-plugins-in-firefox/](https://blog.mozilla.org/futurereleases/2015/10/08/npapi-plugins-in-firefox/) said "[Mozilla] will continue to support Flash within Firefox as an exception to the general plugin policy." Both URLs were as accessed 10-8-17. Also on that day, I visited YouTube and Yahoo Finance and played something on each, and they ran, but they didn't say if Flash was running. Assuming Flash is running, I don't know how to tell if Flash is running on my machine or on a remote server (I tried Googling to find out). Sometimes, I try to run something and can't because the page says Flash is outdated, but I can't remember where that happened, so I can't reproduce it now. I looked at a Youtube page's source code but could not determine anything on point.

---

### Post by ajgreeny on 2017-10-09
Run command ```
dpkg -l *flash*
```
That will tell us exactly what you have installed.

---

### Post by &amp;KyT$0P# on 2017-10-09
> **Nick Levinson said:**
> This is interesting: In </usr/share/app-install/desktop/>, I don't see flashplugin-installer.desktop with my eyes, but Search for Files lists it in a search only for "flashplugin" (without quote marks) and a terminal lists it, as does the paste.ubuntu.com list, as you noticed. Then I eyeballed the folder again and found "Adobe Flash plugin" (without quote marks); according to Properties, the Comment is "Installer for the Adobe Flash plugin for Mozilla" but Properties does not list the name found in the terminal or search. Both purported files are the same size and have the same last-modified date-time and seem to be the same file.
Yes it is the same.  Some file managers display .desktop files by the "Name" line written inside them, instead of their actual file name.  To see the real file names, use Terminal,
```
ls -la
```

>  visited YouTube and Yahoo Finance and played something on each, and they ran, but they didn't say if Flash was running. Assuming Flash is running,
Why would you assume that?

---

### Post by mc4man on 2017-10-09
> **Nick Levinson said:**
> 

Mozilla says we do have Flash in Firefox. [https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems) offered a Flash test page; I tried it and did not get the negative statement Mozilla described for not having Flash. [https://blog.mozilla.org/futurereleases/2015/10/08/npapi-plugins-in-firefox/](https://blog.mozilla.org/futurereleases/2015/10/08/npapi-plugins-in-firefox/) 

That adobe page will tell & show you outright.
screen 1. no flash
screen 2 outdated flash
screen 3 current flash
go take a look & you'll know what's up, odds are on scr. 1

---

### Post by vasa1 on 2017-10-09
> **Nick Levinson said:**
> ...
Mozilla says we do have Flash in Firefox....What does that mean to you? Does it imply that some sort of Flash player is part of Firefox? That isn't the case AFAICT and I didn't see how one could conclude that "we do have Flash in Firefox" from the link provided.

And if by> I guess that if Flash is embedded in another program then a totally different name is possiblein post #5, you feel that Flash is secretly being provided by some software then the standard means of determining whether Flash is on your system may not be enough. You may have to get the help of forensic experts.

BTW, if some visual content is playing in a browser, a right-click on it may tell you if Flash is being used. Here's what I see with no Flash or Adobe software on my system, AFAIK:


And you could visit [https://www.youtube.com/html5](https://www.youtube.com/html5) for more.

---

### Post by Nick Levinson on 2017-10-10
This is getting to look ambivalent. The Adobe test suggested above indicates I don't have Flash in Firefox. (Right-clicking a running YouTube video didn't lead me to an obvious answer.) But, according to Mozilla, "[b]eginning in Firefox version 52, support for NPAPI plugins in Firefox has ended, except for Adobe Flash." ([https://support.mozilla.org/en-US/kb/npapi-plugins?as=u&utm_source=inproduct](https://support.mozilla.org/en-US/kb/npapi-plugins?as=u&utm_source=inproduct) (as accessed 10-10-17).) While one could interpret that as meaning that Flash may not be present, I think the stronger case is that the statement means Flash is present (I don't know why else to support NPAPI plugin capability just for Flash). I may have to ask at a Mozilla forum.

The reason for assuming Flash was running for YouTube and Yahoo Finance is that I think that's what those two pages use. Anyway, my statement was conditional and not a declarative that Flash was running on either page. However, I forgot about the HTML5 player. [https://www.youtube.com/html5](https://www.youtube.com/html5) (10-10-17) doesn't mention Flash; it seems to adapt to my browser, suggesting that it doesn't see Flash in my browser. I looked at one vendor's site (jwplayer.com) without creating a login and didn't see system requirements, but my impression of the site is that it's for installation on servers, not on clients. But since I've repeatedly seen an inability to play a video because my Flash was outdated and an invitation to get something new (I have a couple of active laptops and have recently used several Linux distros, new and old), my guess is that Flash is in use. To resolve whether I have it or not, since I get different results with different HDD and live-disc OSes, I may need to await another failure to play a Flash movie to find out what's going on.

Output of "dpkg -l *flash*" (without quotation marks):

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  adobe-flashplu <none>       <none>       (no description available)
un  gnome-session- <none>       <none>       (no description available)

I proofread the output. The capitalization is so in the original.

If Flash is included, I don't think it's included secretly, like viri, but that it may be included merely in a manner to discourage or prevent removal by users or admins. In Firefox, plugins generally can be deactivated but Flash is not in the list of what can be deactivated. This may not need forensics; it may be that a different name is being used but that someone may know how to deactivate it.

That one file has two names creates a problem that can mislead many people many times in many contexts. I'll think about whether a bug report for the file manager I used would be appropriate.

---

### Post by &amp;KyT$0P# on 2017-10-10
Let's take a moment to recap what has happened in this thread so far.

Nick, you have checked the plugin listing in your Firefox.  You have gone through all your installed packages, multiple times.  You have searched your **entire filesystem** for any traces of Adobe Flash whatsoever.  And you have gone to a Flash test site.

All of your results tell you, you do not have Adobe Flash on your computer.  All that evidence, and you still think you might have a 'hidden Flash', for reasons like these? -
> **Nick Levinson said:**
> The Adobe test suggested above indicates I don't have Flash in Firefox. (Right-clicking a running YouTube video didn't lead me to an obvious answer.) But, according to Mozilla, "[b]eginning in Firefox version 52, support for NPAPI plugins in Firefox has ended, except for Adobe Flash." ([https://support.mozilla.org/en-US/kb/npapi-plugins?as=u&utm_source=inproduct](https://support.mozilla.org/en-US/kb/npapi-plugins?as=u&utm_source=inproduct) (as accessed 10-10-17).) While one could interpret that as meaning that Flash may not be present, I think the stronger case is that the statement means Flash is present (I don't know why else to support NPAPI plugin capability just for Flash). 

... it may be included merely in a manner to discourage or prevent removal by users or admins. In Firefox, plugins generally can be deactivated but Flash is not in the list of what can be deactivated. 

This has gone beyond my ability to help, sorry.

---

### Post by again? on 2017-10-11
> **Nick Levinson said:**
>  ......I've repeatedly seen an inability to play a video because my Flash was outdated and an invitation to get something new......
What you want to do is give a link to a site that tells you your flash is outdated when I doubt it's even installed.
Many suspect streaming sites will tell you your flash is outdated to entice you to download malware disguised as the latest flash.

This shows for my system with adobe-flashplugin and google-chrome installed.
```
glen@GU17:~$ **sudo find / -name *flashplayer.so**
/home/glen/.config/google-chrome/PepperFlash/27.0.0.130/libpepflashplayer.so
/usr/lib/adobe-flashplugin/libpepflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
```

---

### Post by vasa1 on 2017-10-11
TCM's an apparently genuine site. The tooltip for the link points to a apparently legitimate download site for Flash.

---

### Post by again? on 2017-10-11
> **Nick Levinson said:**
> I want Adobe Flash gone, because it's a security risk. A recent update to my Linux installation said it was adding Flash or updating it. But I can't find it. I assume it's embedded in something else. How do I find it or verify its absence?
You may also want to go back to this first post and check your apt history for flash.
You can look in /var/log/apt/history.log for anything flash related.
I believe a new log file is created monthly so you may have to look in /var/log/apt/history.log.1.gz
Navigate to the files in your file browser
or
Command line search:
```
grep flash /var/log/apt/history.log
```

To search in the most recent gzipped log use zgrep
```
zgrep flash /var/log/apt/history.log.1.gz
```

---

### Post by Nick Levinson on 2017-10-13
I don't think I visit streaming sites but I do visit news sites among others and I don't remember which sites refused to play Flash without updating. I've never acted on the invitations but, now that you mention it, I'd like to see what domain is in any such link.

The TCM domain is owned, essentially, by Turner Broadcasting System, Inc., per Whois, so I think it's legit.

The history.log and the history.log.1.gz and history.log.2.gz files (that's all I have and I haven't knowingly deleted any) came up with nothing for the string using either CLI or GUI and searching. Maybe the message about updating should have been phrased conditionally, that the installer was updating Flash if it finds Flash, but I wasn't phrased that way.

@halogen2: I appreciate your summary of evidence, but that Mozilla says it supports Flash in Firefox is important and I did say, next to what you quoted, "I may have to ask at a Mozilla forum." That's not illegitimate; they may have a novel explanation for all their support and yet not having Flash, if that's the case. (A quick search in Mozilla for Flash for Firefox lists hundreds of results, some from this year.) We also have not eliminated that it's not using a file with "flash" as a string in its name; perhaps it's in a wrapper. The searches of my hard drive included an erroneous search, as previously noted. I don't mean to frustrate anyone; I just tend to try to be precise. Thank you for having advised; it was indeed helpful.

Mozilla has another Adobe page for checking whether Flash is installed (and if enabled) ([https://support.mozilla.org/en-US/questions/1179583](https://support.mozilla.org/en-US/questions/1179583) > 2d reply > link to [http://helpx.adobe.com/flash-player.html](http://helpx.adobe.com/flash-player.html) (both as accessed 10-13-17)).

I checked two machines. The Ubuntu one, which this thread is about, does not have Flash in Firefox v56.0 (64-bit). The PCLinuxOS (2016) one, which this thread was not about, has Flash in Firefox v47.0.

That other machine not being an Ubuntu platform, the same terminal commands don't work there (I tried), but I'll deal with that.

Thank you very much. You all helped.

Since this started because Ubuntu said that it was adding or updating Flash but apparently did neither, before we knew that it was reasonable to be concerned that it was hiding somewhere, and maybe I'll post a bug report on Ubuntu's phrasing. The statement should have been conditional, like, if you have Flash, we'll update it, and adding will be if you opt for it.

Thanks again.

---

### Post by Nick Levinson on 2017-11-18
Mozilla edited its articles that formerly gave an impression that Firefox came with Flash already in it ([https://bugzilla.mozilla.org/show_bug.cgi?id=1410669](https://bugzilla.mozilla.org/show_bug.cgi?id=1410669) as accessed 11-9-17). That's cleared up. Thank you.

---

