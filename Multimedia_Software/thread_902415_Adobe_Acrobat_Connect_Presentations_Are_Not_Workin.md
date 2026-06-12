---
title: "Adobe Acrobat Connect Presentations Are Not Working for Me"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Jamie Jackson on 2008-08-27
I have not been able to watch Adobe Acrobat Connect recorded presentations in Ubuntu.

In Windows, if I hit a presentations's link, I get:
[INDENT]Adobe Acrobat Connect Pro Meeting
Loading...
Loading... done
Connecting...
Then, the presentations starts
[/INDENT]

In Linux (Firefox), I get all of the above, except that it stays on "Connecting..." and the presentation never starts.

Here's an example presentation link: [http://my.adobe.acrobat.com/_a227210/p59578003/](http://my.adobe.acrobat.com/_a227210/p59578003/)

FWIW: I get a Firebug error notice when I hit that link in Firefox on Ubuntu. (I don't know if this is helpfulpertinent/ or not.)
```
 [Exception... "Component is not available" nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)" location: "JS frame :: file:///usr/lib/firefox-3.0.1/components/nsSessionStore.js :: sss_saveState :: line 1896" data: no]
this._writeFile(this._sessionFile, oState.toSource());
```

Am I missing something?

---

### Post by orsenthil on 2009-05-18
Were you able to get this working? I am still facing this problem in Ubuntu 9.04.

---

### Post by orsenthil on 2009-05-20
In my case, I was using Ubuntu x86_64 and this problem was resolved when I uninstalled the flashplugins from ubuntu repository and used the 64 bit plugin from adobe ( [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz))

Thanks,
Senthil

---

### Post by hoffman462 on 2009-09-27
I'm seeing the same problem on Firefox 3.014 with Ubuntu 9.04.
I installed flash by following this thread's instructions:

[http://ubuntuforums.org/showthread.php?t=602509](http://ubuntuforums.org/showthread.php?t=602509)

Which basically says 
"sudo apt-get install flashplugin-nonfree"

Curious if anyone has any thoughts?

---

### Post by hoffman462 on 2009-10-17
Ok,
I've tried various approaches to this, including those described in this thread, as well as here:

[http://www.connectusers.com/forums/cucbb/viewtopic.php?id=2086](http://www.connectusers.com/forums/cucbb/viewtopic.php?id=2086)

When I change my flash players configuration, quite a few things tend to break, strangely --- picasa seems to get uninstalled.... I don't know why.


As a *work-around*, I was able to get this working by installing Virtual Box OSE, and running a Windows XP 32 bit Machine, with Adobe Flash Player and hitting the URL in question.

This is the URL that is hanging at a green bar for me:

[http://apus.acrobat.com/exploringtheclassroom/](http://apus.acrobat.com/exploringtheclassroom/)

--- I think that this is a problem?

---

