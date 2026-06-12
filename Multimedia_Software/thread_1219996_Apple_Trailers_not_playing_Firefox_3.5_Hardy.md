---
title: "Apple Trailers not playing Firefox 3.5 Hardy"
date: 2009-07-22
forum: Multimedia Software
---

### Post by steveneddy on 2009-07-22
Sitting around killing time I wanted to see the latest movie trailers.

Apple Trailers is my site of choice.

Using FF 3.5 I cannot view the trailers.

Using FF 3.0 I can view the trailers.

I tried viewing about 10 different trailers with the same results. Box open to play and only black, no loading or other GUI activity in video window.

All codecs updated and OS is complete up to date.

FF 3.5 installed with ppa and is version 3.5.2pre.

FYI - video and sound OK on You Tube and Flash works on all web sites.

Any help appreciated.

EDIT: I disabled Dowmload Helper and Addblock Plus and still get the same results.

---

### Post by lovinglinux on 2009-07-23
Search for the word "quicktime" in the Troubleshooting section of the  [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683) and you will probably find a solution.

---

### Post by steveneddy on 2009-07-23
> **lovinglinux said:**
> Search for the word "quicktime" in the Troubleshooting section of the  [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") and you will probably find a solution.

OK - great answer - let me give a little history - I have been running Ubuntu since 5.04 and although I am no expert I have all of the multimedia codecs installed - or did you miss that part in my original post?

> All codecs updated and OS is complete up to date.

Now - as I said before - it was working previously and even works on FF 3.0 but for some reason I have recently encountered this issue.

I assure you that it is not a codecs issue unless there is a codec specifically for FF 3.5.

I have read limited queries to the same issue on Google but nothing really helps my situation.

I know I'm not the only one with this issue, but I also realize that  it is not a very wide spread issue either.

I will probe the Mozilla forums when I get time I suppose.

Cheers.

---

### Post by lovinglinux on 2009-07-23
> **steveneddy said:**
> OK - great answer - let me give a little history - I have been running Ubuntu since 5.04 and although I am no expert I have all of the multimedia codecs installed - or did you miss that part in my original post?

No, I didn't miss that, that's why I told you to look at the Troubleshooting section, not the installation section. This is what you would have found:

> **ubuntu-freak said:**
> 
**[COLOR="DarkRed"]APPLE TRAILERS[/COLOR]**

For those of you recieving the message "Get the latest Quicktime", when you try to view some trailers (or other non-apple.com Quicktime videos), navigate to "Places > Home", then in the file browser menu, navigate to "View > Show Hidden Files", and tick that option. Within your home directory, navigate to ".mozilla > firefox > ??????.default" and find the file named "pluginreg.dat". Right-click on that file and then choose to open it with a text editor. Alternatively, you could open the terminal and enter a command like the following:

**gedit ~/.mozilla/firefox/??????.default/plugingreg.dat**

**[COLOR="darkred"]Note:[/COLOR]** Make sure you replace "??????.default" with the exact name of that folder.

Once you have opened that file with a text editor, search for "QuickTime Plug-in 6.0 / 7:$", then copy and paste "QuickTime Plug-in 7.0 / 7:$" directly above it, but without the quotation marks of course. Close and save, then restart your web browser.

Since you are running Firefox 3.5, your current profile folder resides under ~/.mozilla/firefox-3.5 not ~/.mozilla/firefox. That's why you can view trailers in Firefox 3.0 but not in Firefox 3.5. You need to update the plugingreg.dat in the ~/.mozilla/firefox-3.5 profile.

Happy now? :P

---

### Post by steveneddy on 2009-07-24
I guess that's what I get for being a smarty pants.

I looked in that file initially and it said:

```
QuickTime Plug-in 7.2.0:$
```and I thought that would be a newer version - don't need to change that.

After your post I changed it anyway just to see what would happen.

It works now.

You were right. I was incorrect in assuming this would not work.

Thanks.

Cheers

---

### Post by tahicks on 2009-08-28
I have the same problem, however, I'm running Firefox 3.0.13 on Ubuntu Hardy (8.04).  Using the suggested change in the pluginreg.dat  did not work however.

Not sure this matters, but for completeness, the Firefox 3.0.13 version of the .dat file contained the string "QuickTime Plug-in 7.2.0:$" as you found in version 3.5.

I guess I'll keep digging for a resolution.  Quicktime payback within the Firefox browser has worked in the past...

---

### Post by Banthaman on 2009-10-27
I'm running Firefox 3.0.13 on Ubuntu Hardy (8.04) also. I have mplayer the mozilla mplayer plugin and have attepted to add the line:

 QuickTime Plug-in 7.0 / 7:$

above the 6.0 line. I save it successfully however when I close and restart the browser it reverts back to only having the 6.0 line and not the edited version. I did notice while editing this file states "Generated File. Do not edit." I can only assume that on restarting the browser it regenerates a new file overwriting the changes. I'm not sure how to correct this though.

---

### Post by boulderbum on 2009-11-07
Having the same problem with firefox 3.0.15  the pluginreg.dat file has two lines that refer to Quicktime  one says:
QuickTime Plug-in 7.4.5:$

The other further down now says:
QuickTime Plug-in 7.0/7:$

Trying to add a line doesn't help as the application only keeps one line in this file when it resaves it.

Still no joy.  Mplayer was running fine with quicktime video until about 3-4 weeks ago. I am super frustrated with tis problem as there seems to be know apparent cause for the problem...  I have ripped out and reinstalled all packages and codecs in varying order and still no joy. 

Any other ideas?

---

### Post by cybergalvez on 2009-11-08
Thank you you fixed my problem! BTW I had several conflicting plugins installed, I removed all the conflicting one and left mplayer, now everything works great!

---

