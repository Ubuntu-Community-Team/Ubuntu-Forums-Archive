---
title: "Will Beryl work?"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by jdhore on 2007-03-09
Hello all, i really hope someone can help me with this.

I'm running Edgy on a 2.4GhZ P4 with Nvidia Geforce4 MX420 Go graphics (32MB) on the Nvidia 3D 1.0-9631 driver. I want to get Beryl working with AIGLX and i also use dual-monitor (Twinview, 2 x 1024x768 ). I've gotten Beryl + Aiglx working with the same driver with a single monitor, but not with both (driver issues). I have 3 questions:

1. Will my video card have the power to run Beryl on dual-monitor?
2. If not, can i have Beryl only give me the fun effects on one monitor?
3. If my video card can handle Beryl on both displays, do i have to do any special configuring to it (Beryl)?

---

### Post by jamienos on 2007-03-09
> **jdhore said:**
> Hello all, i really hope someone can help me with this.

I'm running Edgy on a 2.4GhZ P4 with Nvidia Geforce4 MX420 Go graphics (32MB) on the Nvidia 3D 1.0-9631 driver. I want to get Beryl working with AIGLX and i also use dual-monitor (Twinview, 2 x 1024x768 ). I've gotten Beryl + Aiglx working with the same driver with a single monitor, but not with both (driver issues). I have 3 questions:

1. Will my video card have the power to run Beryl on dual-monitor?
2. If not, can i have Beryl only give me the fun effects on one monitor?
3. If my video card can handle Beryl on both displays, do i have to do any special configuring to it (Beryl)?

I know for a fact, that the MX420 run's the fancy effects - i am running beryl on that card now and it's real smooth the only thing's that might not work is snow/water because of pixel-shaders i think.

Not to sure about dual display's but i see no reason why it wouldent.

---

### Post by jdhore on 2007-03-09
UPDATE: for some reason, Beryl isn't really starting, it installs correctly (in XGL) and XGL runs fine, i just get this when i try to start beryl-manager:

Root window size (2048/768 ) is bigger then maximum texture size (2046x2046)

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  28
  Current serial number in output stream:  30

could someone please help me?

---

### Post by jamienos on 2007-03-09
> **jdhore said:**
> UPDATE: for some reason, Beryl isn't really starting, it installs correctly (in XGL) and XGL runs fine, i just get this when i try to start beryl-manager:

Root window size (2048/768 ) is bigger then maximum texture size (2046x2046)

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  28
  Current serial number in output stream:  30

could someone please help me?

Never had this myself, but i did some searching and found this [TOPIC(This is a url)]("http://forum.beryl-project.org/viewtopic.php?f=36&p=24988") 

Quote from the post adamk replyied

> You haven't given us much to go on. No information about your video card or drivers, for example.

However, assuming your drivers are installed properly, it would appear that your video card only supports a maximum 3D texture resolution of 1024x1024, and your running your display at 1400x1050. Sorry, but you'll need to drop your screen resolution to get beryl working.

So which basicly, if i understand correctly you are running a resolution of '2048/768' so changing it to '2046x2046' might solve it.

It's worth a try, but dont take my word for it as i said i have never had this and am only telling you what i found on the beryl forum hope it all works out for you :)

Edit: i see your's is 2048 and the one it is saying is 2046 so its 2 over, maybe changeing to 2046x768 may work if this is the solution

---

### Post by jdhore on 2007-03-09
> **jamienos said:**
> Never had this myself, but i did some searching and found this [TOPIC(This is a url)]("http://forum.beryl-project.org/viewtopic.php?f=36&p=24988") 

Quote from the post adamk replyied



So which basicly, if i understand correctly you are running a resolution of '2048/768' so changing it to '2046x2046' might solve it.

It's worth a try, but dont take my word for it as i said i have never had this and am only telling you what i found on the beryl forum hope it all works out for you :)

Edit: i see your's is 2048 and the one it is saying is 2046 so its 2 over, maybe changeing to 2046x768 may work if this is the solution

well...on more of a update, i can't lower my resolution and still dual-monitor, but that's not really my problem...in both Beryl and Compiz, i get no window manager (a.k.a. no title bar)...i've tried starting the gnome-compiz-manager manually and emerald/helio manually and no luck :(

---

