---
title: "Grab the originally uploaded file from Veoh"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by netyire on 2008-01-13
[SIZE=1][COLOR=Silver]Adapted from [http://spotlesschristmas.blogspot.com](http://spotlesschristmas.blogspot.com)
Source Code Provided![/COLOR][/SIZE]
----------------------------------------------------------------
[SIZE=3]** Download from Veoh without VeohTV**[/SIZE]
[B]
Veoh, What Art Thou?[/B]
Veoh has great content and it also stores the uploaded video file in its original form. Thus, you can enjoy Veoh's quality content in a quality format. Sadly, Veoh has had some unattractive policy changes:

1) Veoh cuts down >20min footage to a 5 minute preview, demanding that you download VeohTV to view the whole clip.
2) Veoh no longer allows you to download the original file with VeohTV
3) Veoh can delete any video file you downloaded with VeohTV, so long as you haven't moved it

These changes are significant - because of them Veoh is now a restricted service whereby you need to download VeohTV to watch anything useful. Furthermore, although the quantitative collection of videos are still available through VeohTV, they are no longer offered as high quality downloads of the original file.

Translation:

1) Its hard to access the content
2) You'll get poor quality content
3) Veoh can restrict your access to specific content at anytime
[SIZE=2]
** Preserving Quality Access**[/SIZE]
Since VeohTV is a farce and Veoh itself is unbelievably useless, a call for more accessible content of a higher caliber is justified. People should be able to access the qualitative and quantitative content again - and without any restrictions or loss of freedom. In other words, you should be able to easily download the full footage of anything you can find on Veoh - and in its high quality, original file format. In addition, you should be able to do this without having any totalitarian government (eg: veoh) enforcing police state policies on you. Thus we have our aims:

1) Full access to the entire spectrum of content on Veoh
2) Direct access to the content in its original form
3) Freedom and anonymity, without having to rely on VeohTV

In the view of these aims, I would like to introduce you to [http://www.ninjathis.net](http://www.ninjathis.net), a website which will allow you to simply copy and paste the address of the playing content on veoh in order to watch and download the full quality clip. Thus achieving all of our 3 targets.

Sounds great? It is, but theres still 1 more thing - your reliance on ninjathis. This definitely isn't good, therefore a localized program is in order. Here's a link to a stand alone python program packaged with pyinstaller that will allow you to retrieve the link to the original file by typing in the PermaLinkID of the playing video. For example in [http://www.veoh.com/videos/gg12356q22?searchid=3222&rank=3](http://www.veoh.com/videos/gg12356q22?searchid=3222&rank=3), the PermaLinkID is gg12356q22.

You can download the standalone program here: [http://tinyload.com/ZU3eyx](http://tinyload.com/ZU3eyx)
Just enter the LinkID and hit generate.
[B]
Takeaway

[/B]1) Don't use VeohTV
2) Use this program to get the original quality clip uploaded and to get the full clip (no five minute restrictions)
3) Download the exe and use wine (in the repos) or download the **attached .py file and just double click or open it with python.**

---

### Post by javaJake on 2008-01-14
Thanks very much for the python script. It worked to perfection! :D

---

### Post by lafouine on 2008-01-20
thx

---

### Post by nstamato on 2008-01-29
How did you guys get the video? I downloaded the python script, ran it, got the real address but then couldn't get it neither via firefox or wget. In wget I got a FORBIDDEN message.

---

### Post by javaJake on 2008-01-31
They probably heard about this and fixed it up so it won't work. :(

I can't try it myself at the moment.

---

### Post by eightdollarbeer on 2008-02-03
this need to be made a firefox extension.

---

### Post by darkwoofe on 2008-02-20
Is this still working?

---

### Post by javaJake on 2008-02-20
Nope, apparently they figured it out. Now mplayer says "403 Forbidden".

---

### Post by petit_prince on 2008-04-07
Apparently the approach provided in this thread is not working any longer. While doing a little bit of research, I found out that there is another solution hosted on google codes, which isn't working either, BUT in their bugtracking system I found a link to
[http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG]("http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG") which DOES seem to work.

---

### Post by unbehagen on 2008-05-04
I just ported the download part of the this VeohDownload program to a few lines python. Grab it here: [http://theendofthelongestline.de/blog.html](http://theendofthelongestline.de/blog.html)

---

### Post by unbehagen on 2008-05-09
I just wrote a new program which works as a proxy and also supports NinjaVideo. Now you can't just download, but stream high quality content veoh videos. Grab the script here:
[http://theendofthelongestline.de/blog.html](http://theendofthelongestline.de/blog.html)

---

### Post by achikjep on 2008-05-09
> **unbehagen said:**
> I just wrote a new program which works as a proxy and also supports NinjaVideo. Now you can't just download, but stream high quality content veoh videos. Grab the script here:
[http://theendofthelongestline.de/blog.html](http://theendofthelongestline.de/blog.html)

thx ... great program ... it run smooth for ninjavideo but i get "Error code explanation: 404 = Nothing matches the given URI." for veoh ... log message are showed "Could not get ninja ID." which is mean that this program cant recognize veohID ?

---

### Post by McMagic on 2008-05-13
Thanks so much! Ive been trying to get ninjavideo vids to work on gutsy for some time!

---

### Post by logari81 on 2008-05-18
The python skript for veoh works fine for me. You are great. I hope it lasts some time until the veoh people change their system once again to block workarounds like yours.

I wonder why people intent to install the veoh client under linux if there is always a solution to get the video on their disk.

---

### Post by beefcurry on 2008-05-18
Great script, helped alot with NinjaVideo.

---

### Post by 123b123 on 2008-05-29
I have direct link when I press Genarate.([http://ex-cache.veoh.com/cache/external/3989bc6bcb3dfae656783f8ea5d9dc67885459b0.avi?permalinkId=v67729797BBqzQ45](http://ex-cache.veoh.com/cache/external/3989bc6bcb3dfae656783f8ea5d9dc67885459b0.avi?permalinkId=v67729797BBqzQ45)). But when I copy and paste to IDM and press Start Download, I see error message "The server peplies that you don't have permissions to download this file. Why I don't have permission to download this file ?

---

### Post by durand on 2008-06-02
> **unbehagen said:**
> I just wrote a new program which works as a proxy and also supports NinjaVideo. Now you can't just download, but stream high quality content veoh videos. Grab the script here:
[http://theendofthelongestline.de/blog.html](http://theendofthelongestline.de/blog.html)

Thanks a lot! Thanks to netyire for the original script as well.

---

### Post by netyire on 2008-06-04
Its been some time since the thread was put up and it looks like a lot has happened in such a short span of time. For one Veoh appears to have gotten a heads up on the methods used to circumvent its proprietary framework of video distribution. I haven't been keeping up with the latest exploits which still hold true in spite of the newest updates on Veoh's end - and as such the script is in disarray (urm... alright! I'll say it - its useless) Apologies for this lack of functionality.

I'm glad that other people still maintain an active interest in accessing the original content and I'm very grateful that they are willing and generous enough to post their discoveries on this thread. Please continue to do so, it makes Veoh on linux a whole lot more painless.

Finally if ever software no longer exists to automate the quite complicated procedure of obtaining the original content though you still have wind of the method involved, please post it here and I'll try writing one. And I'm sure a lot of other people would just love to have a go as well =-)

---

### Post by z0mbie on 2008-06-09
This script works fine, get the updated version here:

[http://code.google.com/p/veohproxy/](http://code.google.com/p/veohproxy/)

Just follow the directions.

---

### Post by durand on 2008-06-09
He meant his script, not veoh proxy

---

