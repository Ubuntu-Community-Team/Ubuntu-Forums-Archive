---
title: "skype freezing and even crashing edgy."
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by jouka on 2007-03-08
Hi, I noticed that Skype software version for linux is indeed handicapped version.

Me and my gf both have ubuntu edgy versions running and well. We're using Skype to get in touch now because of the distance we have in between. Okay well that's all about the romance, this aint no novel.

We've both experienced system freezing (for around 10-50 seconds) when making/receiving calls. It's the moment after you've pressed Call button. Or even when another one logs in to Skype and u see the pop up window at the right bottom screen.
I was just okay with freezing problem but tonight I saw something that really got me frustrated.

I was logged off (program was on though) from Skype and my gf didn't notice it and she made a call for me. Then her computer froze and didn't recover. She called me with her mobile phone and told about this issue. Told her to try ctrl+alt+f2 to see if she could get in to a console, it was a no go. She couldn't shut down X ether (ctrl+alt+backspace). Then I tried to ping her IP and it was responding, but I couldn't log in with ssh. Okay then I logged in to Skype and called her because I thought there would've been a slight chance of getting revived connection and my gf computer back from the grave...

My computer froze! I was like ffs and waited, nothing happened. Couldn't go to console nor shut down X. I cursed and pressed reboot that I haven't used for awhile since my long gone windows partitions. When my computer was booted my gf told me her computer woke up and started working. What the hell? So after her computer noticed my IP was not getting connection it gives up? Buggy software, skype is.

Anyone else experienced similiar problems? I think this is Ubuntu+kernel+skype problem because the freezing is only happening with ubuntu users if I'm correct (read some topics about it.)

I'm not a hacker myself so that's why I can't really help resolving this matter very much but I hope it would be fixed if it's common.

---

### Post by NT4usB on 2007-03-08
Appears to be a well known problem.
[skype freeze]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%2Bskype+%2Bfreeze&btnG=Search")
I have it on my Edgy box. Haven't actually used it yet though. I only have one friend and they haven't been on line lately...

---

### Post by sc00ter on 2007-03-20
I was getting the same problem, I applied this "work-around": 
[URL="http://ubuntuforums.org/showthread.php?p=2165712"]
http://ubuntuforums.org/showthread.php?p=2165712[/URL]

If you launch Skype via it's application icon, then:

From a Terminal window type: 

[FONT="Courier New"]sudo gedit /usr/share/applications/skype.desktop[/FONT]

change the **Exec** line to:

[FONT="Courier New"]Exec=nice -n 19 skype[/FONT]

and save the changes.

Restart Skype.

---

