---
title: "TORK:  TOR Stopped Talking To Us"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by coljohnhannibalsmith on 2010-03-19
I'm using Ubuntu Hardy x64 and when pressing "Play" in TORK, I get the following Message:

*TOR Stopped Talking To Us!!

*Message: Did Something Happen To Me?

*This Means: Try Starting TORK Again.

TOR Starts up in the background.  and I have also tried killing TOR and then restarting it with Vidalia and verifying that TOR is running.  I've also tried using the Wizard to configure TORK to no avail.  It also does'nt seem to be able to write to the "torrc" file.  Also, when I select Tools>Browse TOR Network Status, I get the following message:

*Could not launch the browser:

*Could not find service "kfmclient."

I suppose this could mean that I need to install some elements of KDE, but I have several KDE applications running on my installation, such as Amarok, with no complications.

Any suggestions?


Thanks, Hannibal

---

### Post by light-vessel on 2010-11-17
Although this problem looks like it happened a while ago, I have  recently found the same problem, and I can't see any answers to it yet.

Even as a beginner, I have a theory, and that's that Tork is looking in  the wrong place for files. When I went through the setup procedure, all  the suggested file locations for Tor's and Privoxy's configuration files  were wrong and I had to go and hunt them down and type them in  manually. My Tor and Privoxy files are all in init (is this something to  do with these programs running on startup?)

Because I'm a beginner, I wouldn't know how to investigate this theory  and I would have thought someone else might have a better one. I  couldn't get Vidalia to work and now I can't get Tork to work, so I have  to use Tor without a nice GUI to make things easy or practical.

Just a footnote question: Why did I have to allow script from google-analytics to make this post work?

---

