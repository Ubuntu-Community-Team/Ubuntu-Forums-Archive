---
title: "ATI - Resolution gone.  fglrx errors after install"
date: 2008-08-19
forum: Multimedia Software
---

### Post by barronmb on 2008-08-19
My Kubuntu (2.6.24-19 --- no upgrades available) box was working on a previous version of the ATI proprietary driver (8.6).  I recently installed an nVidia card and got it working.. but alas the card has issues and must be RMA'd.  So here is where the fun begins.  

I yanked out the nVidia and reinstalled the ATI (Radeon 9800se AGP).  After that I booted up and the desktop was normal (had 1650x1080 res.. etc but no accelerated graphics).  I then attempted to install the latest ATI driver 8.7.  Once installed I got the flicker screen of death.  The screen would blink a couple of times.. then just stay dark.  Could not ctrl+f1, f2 etc to get to CLI.  

I then booted into recovery.. fixed X.  Again same resulting desktop.  So I pulled up another how to and followed step by step (from the wiki.cchtml site).  Once rebooted.. you guessed it.  Flicker and black out.  So then I decided to boot into root CLI from recovery.  Followed the troubleshooting steps from the wiki entry and removed the fglrx drivers et al.  

Once completed I attempted again to install via the wiki's instructions.. it failed.  So I tried the direct install (you know.. the automated proprietary install)... same result yet again.  Remove it again and then tried the opensource.  Once installed.. upon reboot.. yup.. I get flicker... then in the left top corner I get (in between flickers):

"fglrx (8.512): Already installed on this Kernel"

So I remove it all (in recovery mode) yet again.. then try the envy install... Same result:

"fglrx (8-6): Already installed on this kernel"

I even tried the old driver 8.6 again and it failed and posted the same fglrx error (for 8.501).

Meanwhile.. If I set the card in System Settings to ATI (fglrx) or (vesa) and hit test.. it fails every time.  I am stuck at 1024x768 on my 22" widescreen.  I have tried numerous settings in system settings and they all failed... some just flicker then come back saying it won't work.. others flicker for a sec.. then pull up the checker-board backround (B&W) and the large X for a pointer (which will sit there until I ctrl+alt+backspace)

Any help available on this?

---

### Post by barronmb on 2008-08-21
Bump in the hopes that there's help out there.

---

### Post by barronmb on 2008-08-22
Bump yet again.  Hoping for some help here....

---

