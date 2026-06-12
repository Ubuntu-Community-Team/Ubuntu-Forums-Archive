---
title: "whats wrong with my tor?"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by MitchAlbertz on 2013-04-25
I have ubuntu 12.04 on my series 5 chromebook, and before I downloaded for windows and ran it through wine (i was having troubles downloading tor for actual ubuntu) it worked fine, i got it to download that actual ubuntu version, and vidalia pops up when i click on it and says its connected, BUT the browser never shows up, any reason on how to fix this?
AND another question, now my .exe tor wont work either, when it connects it says i need a password, i have used my internet password and my computer password but nothing works.
Any suggestions would be greatly appreciated.

---

### Post by benj23673 on 2013-04-25
If tails isn't an option for you (you should look into it), I think installing tor via the command line will be best if you can not do that downloading form the tor website will give you the .exe that you can run every time you click on it. as far as the password goes I have no clue it has been a while since I have actually used tor.

---

### Post by clearski on 2013-04-25
If I understand correctly, what you're saying is that you locked Vidalia to your Unity Launcher, but it won't start, just keeps blinking.

Here's how you can bring it to your Launcher.

Let's suppose that your path to tor is /home/user/Desktop/tor-browser_en-US

Go to Ubuntu Software Center and search for Main Menu. Install it, then open it from the Dash. Go to Internet menu, then choose New Item. Type: Application, Name: TorBrowser, Command: /home/user/Desktop/tor-browser_en-US/start-tor-browser

You can also click on the icon on the left side of Launcher Properties and choose an icon of your choice because the Vidalia default icon won't be set (for a reason I don't know and really don't mind - in my case :) ).

Close the Launcher Properties. 

Now look for TorBrowser in your Applications (using Dash) and drag it to your Launcher. Next time you click on the TorBrowser icon it will launch Vidalia and Firefox.

Before you start Vidalia from Launcher, just make sure there's no other process started.

ps ax #get all PIDs for Vidalia & Tor
kill PID #for any Vidalia/Tor related PID

Hope this helps.

---

