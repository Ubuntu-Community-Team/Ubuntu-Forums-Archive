---
title: "Flash screens have gone blank or inoperative"
date: 2011-02-18
forum: Multimedia Software
---

### Post by pwabrahams on 2011-02-18
Flash (via Firefox) was working until a day or so ago, but now the content that is supposed to be viewable with Flash simply sits there and does nothing or comes up as a blank screen. I've tried several web pages, all with the same problem.  Every indication, including the Adobe test page, shows that Flash is installed, although the Firefox page for "Manage Content Plugins" lists "Gnash SWF Player"as the application for x-shockwave-flash.  If I try to install Flash again, I'm told that it's already installed.  I can disable it in Firefox but I don't see how to remove it altogether so that I can reinstall it (which still might not help).

How can I get my Flash content working again?

---

### Post by ankspo71 on 2011-02-18
Hi,
The problem might be that Adobe Flash and Gnash are conflicting with each other (even though one may be disabled), and it might have started acting up on you when we all got a flash update this week to version 10.2. 

Try the firefox addon called Flash-Aid. 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
This will automatically install flash for you, apply some flash tweaks, and remove conflicting plugins.

Or you can search synaptic package manager and remove all instances of gnash*, swfdec*, etc. 

Hope this helps.

---

### Post by pwabrahams on 2011-02-18
I installed flash-aid,removed gnash and swfdec, and went to one of the problematic web pages.  I got the message "Additional plugins are required to display all the media on this page.", with a button for "Install missing plugins".  If I follow the prompts and select Adobe Flash for the plugin, it goes through a bit of processing and then gives me the message "Package flashplugin-installer is already installed."  So I go back to the web page, and the same thing happens all over again.

At one point I downloaded a package from Adobe, but it wouldn't install because it was an i386 package and I have a 64-bit system (wrong architecture complaint).

Perhaps if I could call flashplugin-installer from the command line, that might help, but it's not an executable file, it seems.

At least, thanks to you, I know what provoked the problem: the latest Flash update.  But I still have no idea what to do about it.

---

### Post by pwabrahams on 2011-02-19
I discovered what I was missing: in the Firefox installation of Flash-Aid. I needed to click on Preferences.  That brought up a number of choices, one of which was to call a shell script for doing the real work.  I did that, and Flash started working -- some of the time!!  On the website of my favorite classical music station, I was able to bring up the greeting and display the screen that shows up when you're playing music -- but no sound there, even though there was sound on the greeting and on the specialized pages that were also available.  On the New York Times website, videos came up but wouldn't play.

The troublesome URL is [http://player.abacast.com/allclassical/allclassical.html](http://player.abacast.com/allclassical/allclassical.html).

This seems even harder to diagnose than the original problem.

---

### Post by no2498 on 2011-02-19
i could see the live stream 
but i use 32 bit and just reinstalled flash last night for a diff site last night

---

### Post by pwabrahams on 2011-02-20
I used Flash-Aid in expert mode and under Installation Options, chose Adobe from Repositories, 32 bit -- which is not the default.  The default is the Beta from Adobe.  Under Removal Options, I checked everything.   And now it works!  Thanks.

---

