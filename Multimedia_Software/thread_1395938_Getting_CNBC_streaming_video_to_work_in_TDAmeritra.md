---
title: "Getting CNBC streaming video to work in TDAmeritrade's Thinkorswim"
date: 2010-02-01
forum: Multimedia Software
---

### Post by mmelnick on 2010-02-01
Hey everyone.

So TD Ameritrade has a trading program called Thinkorswim (build 1585). It's a java program, cross platform for Windows, Mac and Ubuntu. It's a very good program, with a lot of features. I installed it in my  Ubuntu 9.04 and it works well. HOWEVER..
There's one portion of the program that allows you to stream a CNBC live video feed inside the Thinkorswim interface. I went to use it but the play button is greyed out. There doesn't seem to be any way to play the video in the program. When I hit the "pop out" live video button however, my Totem player opens and the video plays fine. This leads me to believe that my Ubuntu install is fine, my codecs are ok, but the TD program just isn't able to find the codec and start video. There's no preferences button to be found in this portion of the program. So I tried contacting their support team. At first they told me to go here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and install the restricted formats packages. I did. Still didn't work. I asked them again on the phone this time, and no one seemed to be able to support Ubuntu..one of their tech people even seemed puzzled when I said UBUNTU until I told them it was Linux lol Anyway, I emailed a 3rd time to a person they suggested on the phone, their "Linux guy". The response I got back was this.

"After checking with our Linux expert,  I found out that it is not possible to run the CNBC feed inside the platform on the Linux operating system.  The only operating system that will run the stream inside the platform is Windows.  This is due to the fact that other operating systems lack a compatible windows media player plug in that would allow the stream to run inside.  Linux and Mac users must run the stream outside the platform in order for it to work.  I appreciate your patience while I researched your issue.  If you need further support, please let us know."

Best regards,
Seth Woerman
Trade Support
thinkorswim from TD AMERITRADE

Ok I find this hard to believe! If Java is a universal platform, and the feed works in Totem fine, how can it not work inside the interface? And how can a huge company like TD Ameritrade distro a program that doesn't work 100% from the getgo? 

Can anyone help me get this to work? i refuse to believe they'd release the software if it didn't work. I just think I can't get at anyone good enough with Ubuntu to support me.

---

### Post by dan@dpopy.com on 2010-03-01
I had the exact same problem. Here is a work around: Open thinkorswim.com and start webbased trading. Start CNBC live tv on the left hand side panel. It should work just fine. If you want you can click on "^" then Open with "Movie Player" so you can close the browser window.

---

### Post by mmelnick on 2010-03-01
Unfortunately thinkorswim is a separate company.. to use their web interface you have to be registered with thinkorswim, and even if I was registered, I wouldn't be able to access my TD Ameritrade account data through their web based interface. Thanks anyway.

---

### Post by bleck on 2010-03-17
The reason it doesn't work is becuase it's not encoded to embed a totem player window into the platform. What's embedded is Windows Media Player and that will not work in any platform but windows.

Popping it out simply sends a link to the stream which opens fine in your movie player. It's a Windows Media stream which is the reason for them instructing you to install the codecs. Sorry, but until the program is developed to handle a flash or java embedded video player it won't work.

Mac users have the same issue and have to use VLC to stream the feed.

---

### Post by muisudad on 2010-10-29
started new thread

---

### Post by Chemham on 2011-03-27
To all,
 
I have just installed Ubuntu 10.04 on two machines. To get Java, on one machine I installed Sun Java 6 and the other Open JDK. The streamer (on either machine) in Ameritrade now will not appear properly.  In order to see all stock entries, I need to use the scroll bars.  In Ubuntu 9.10 it worked properly. 
Any help is appreciated,
Chemham

---

### Post by seaq on 2012-02-03
Hey, I was looking exactly for this issue, I usually open a Trade Architect windows for the CNBC feed and the TS for the tools.

Gonna check the totem trick, didn't new about it.

thks

---

