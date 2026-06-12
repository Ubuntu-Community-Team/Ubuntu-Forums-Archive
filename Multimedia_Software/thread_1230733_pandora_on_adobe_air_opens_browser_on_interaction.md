---
title: "pandora on adobe air opens browser on interaction"
date: 2009-08-03
forum: Multimedia Software
---

### Post by v1nsai on 2009-08-03
It hasn't been easy trying to get pandora on linux without a browser but I got it running with Adobe Air and it works well except that every time I click on it, it opens the pandora site in a browser.

I had trouble getting Adobe Air to run at first before I could even install Pandora, and I had to copy a .so file to another directory so air could find it.  I have been trying to find it to see if removing it would fix it but now I can't remember where I put it and what file it was >.<

Anyway, has anyone else gotten Pandora to run with Adobe Air?  I've trie dall the screenlets but they all have tried to download itunes and won't play anything

---

### Post by v1nsai on 2009-08-06
still haven't figured this out.  I can listen to pandora in the browser but I'm curious how to fix this, I'm sure it isn't too hard I just don't understand how it all works

---

### Post by v1nsai on 2009-08-11
Did a clean reinstall of Adobe Air which worked just fine this time around, reinstalled Pandora and still having the same problem.  I would really appreciate some help :)

---

### Post by looter211 on 2009-10-14
I will post this same link as I did in another user's post (djm277).  Not sure if you have found anything further in your inquiries or if you have given up but perhaps this can shed some light on the subject.  It has, somewhat, for me.

[http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora]("http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora")

In the pandora employee's reply in that blog she states that the beta version of pandora for adobe air was beta and that it was "broken."  how convenient.  now the only way to seemingly get it to run outside a browser (without these conveniences) is through purchasing a pandora one account.  although I am still curious to see what my pandora air app runs like on my ubuntu install at home.  I'm guessing whatever they "broke" was server side though, how convenient, so it might not matter that i've had that installed and working for a year now.  Love the pandora service but until i can get decent work I'm not dishing out 40 bucks a year primarily for the purpose of liberating pandora from a web browser.   my apologies if this turned into a rant, i hope at least some of it was informative.

---

### Post by greg963 on 2009-11-28
You can use mozilla's prism to launch pandora

apt-get install prism
then download the attached file and extract the Pandora.webapp then launch

Or for some more ideas see my script here
[http://ubuntuforums.org/showthread.php?t=1340349](http://ubuntuforums.org/showthread.php?t=1340349)

---

### Post by yblumberg on 2009-12-21
I figured out how to make it work, at least on a mac. If you go to Show Package Contents (by right clicking the application) then Contents>Resources>javascript>main.js and change loader.navigateInSystemBrowser = true; to loader.navigateInSystemBrowser = false;

If you can get to main.js on ubuntu I expect it will work the same.

Open (or reopen) Pandora and try clicking play or next or something. It should work without opening any windows in your default browser. Of note, this will prevent opening ANY external pages. I found that clicking "Your Profile Page" loads the popup blocker warning and prevents the keyboard controls from working until I relaunch the application. I plan to try to find a better workaround if I can, but in the meantime I like this fix. 

For those who are wondering, the reason I prefer the Air app to those created with Prism or Fluid because, among other really tiny things, it has controls I can access in the dock with a right click.

---

### Post by Benjimusprime on 2010-01-12
Hey, this worked great.  Thanks!  I found the main.js in /opt/Pandora/share/javascript/
Works like a charm!

---

