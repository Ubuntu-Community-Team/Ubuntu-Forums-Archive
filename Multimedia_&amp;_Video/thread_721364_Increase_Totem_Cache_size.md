---
title: "Increase Totem Cache size"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by mobrien118 on 2008-03-11
Hello,

Quite simply, I have a file server with videos on it connected to my network "backbone".

My Ubuntu box is on a wireless link to the backbone and gets about 1.5MB/s (12mbps) from the file server. This is fine except for very intense action parts of movies. To remedy this problem I can increase the cache size in VLC (and I believe I can do it in mplayer's config file). Surely there is a way to do this in Totem. I want to stick with Totem as my default media player so any help with increasing the read-ahead cache size of Totem would be greatly appreciated.

Thanks,

--mobrien118

---

### Post by {BzF}~JOKesTER on 2008-03-13
I Have A Solution!!!!

Ok First Open A Terminal.

Now Type:

sudo gconf-editor

And In The Box That Appears Click:

Apps,

Than

Totem

And In The Righthand Pane Find "buffer-size"

Now Double-Click It And Change The Value - Higher Or Lower - {Depending On How You Want It}

Hope This Helps!!!! -{If It Does Hit "Thanks"}

L8rs:)

---

### Post by {BzF}~JOKesTER on 2008-03-13
You Can Also Change The Stream Ahead Of The Player By Changing The Value Of "Network-Buffer-Threshold" Up To A Higher Value

---

### Post by mobrien118 on 2008-03-13
Thanks Jokester.

I actually already discovered that solution but didn't have the chance to post back yet.

Nice work and thanks awarded.

--mobrien118

> **{BzF}~JOKesTER said:**
> I Have A Solution!!!!

Ok First Open A Terminal.

Now Type:

sudo gconf-editor

And In The Box That Appears Click:

Apps,

Than

Totem

And In The Righthand Pane Find "buffer-size"

Now Double-Click It And Change The Value - Higher Or Lower - {Depending On How You Want It}

Hope This Helps!!!! -{If It Does Hit "Thanks"}

L8rs:)

---

### Post by breno leitao on 2008-04-30
Just increment the buffer size and everything goes fine, except the initial delay to start the video/sound. 
I've changed mine from 3 to 10, and it took 40 seconds to start an online radio (instead of 10 seconds using "buffer size" = 3). But I didn't get anymore break during the stream. 

--
Breno Leitão
leitao(at)linux.vnet.ibm.com

---

