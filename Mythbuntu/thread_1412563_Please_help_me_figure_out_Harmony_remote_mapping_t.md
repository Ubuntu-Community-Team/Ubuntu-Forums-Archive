---
title: "Please help me figure out Harmony remote mapping to MCE..."
date: 2010-02-21
forum: Mythbuntu
---

### Post by killabee44 on 2010-02-21
Guys,

I have a Harmony 900 remote. I got it working fine with Myhtbuntu, but the buttons are not quite the way I want them. Here are some of the issues I am trying to solve.

When I change channels, channels do not change until I select the ok button, making it take too long to change a channel. I want to change a channel real time.

I would like a button set up to skip pages when I am using the guide.

I would like to set up buttons to take me directly to Mythvideo, Mythgallery etc. or to skip through them. 


The problem is that I do not have an MCE remote to learn functions from. Your help is appreciated.

---

### Post by kyfehr on 2010-02-21
I can tell you to fix the first issue the channel change then ok issue is a setting in the Settings pages. not sure which one off the top of my head, but it is a setting.

---

### Post by kyfehr on 2010-02-21
also this site might help you
[http://www.mythtvtalk.com/forum/hardware/7871-biggest-baddest-best-remote-control.html]("http://www.mythtvtalk.com/forum/hardware/7871-biggest-baddest-best-remote-control.html")

---

### Post by killabee44 on 2010-02-21
Thanks, Ill be looking into that link. Also, I forgot to mention that I am using a MCE USB infrared.

---

### Post by joho500 on 2010-02-22
> **killabee44 said:**
> Guys,

I would like to set up buttons to take me directly to Mythvideo, Mythgallery etc. or to skip through them. 


You can do this by setting up Global keys in mythtv for these options (I use Mythweb for this) and then map them in your lirc file to the MyVideos, MyMusic buttons of the original MCE remote.

Like this:

begin
   prog = mythtv
   button = MyMusic
   config = $
end

You can than map your Harmony buttons to these MCE buttons.

Cheers,
Joost

---

### Post by killabee44 on 2010-02-23
Ok, I don't quite understand how to do this, but I will research further.. 

Thanks.

---

