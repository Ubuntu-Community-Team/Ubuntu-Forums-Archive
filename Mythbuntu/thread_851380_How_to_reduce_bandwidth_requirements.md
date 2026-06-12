---
title: "How to reduce bandwidth requirements?"
date: 2008-07-06
forum: Mythbuntu
---

### Post by SteveGodfrey on 2008-07-06
I have a Mythbuntu backend with a Nova-TD configured as dual DVB-T standard definition receivers connected via 100 Mbps ethernet. Programmes record and playback well on the backend. I also have a Pavilion laptop running mythbuntu frontend only. I use this to playback recordings and videos from the backend.

The laptop is connected using wireless (11g) which gives me around 27Mbps of bandwidth. Unfortunately this isn't enough to playback recorded TV. If I connect the laptop via 100Mbps LAN it works fine. Is there some way I can reduce the bandwidth requirements? As things are playback pauses every few seconds for the 'network' to catch up. When playing back recorded TV network utilisation is around 25Mbps.

Any ideas, connection the laptop via cat5 is a pain!

Thanks

Steve

---

### Post by mrand on 2008-07-07
> **SteveGodfrey said:**
> I have a Mythbuntu backend with a Nova-TD configured as dual DVB-T standard definition receivers connected via 100 Mbps ethernet. Programmes record and playback well on the backend. I also have a Pavilion laptop running mythbuntu frontend only. I use this to playback recordings and videos from the backend.

The laptop is connected using wireless (11g) which gives me around 27Mbps of bandwidth. Unfortunately this isn't enough to playback recorded TV. If I connect the laptop via 100Mbps LAN it works fine. Is there some way I can reduce the bandwidth requirements? As things are playback pauses every few seconds for the 'network' to catch up. When playing back recorded TV network utilisation is around 25Mbps.

Any ideas, connection the laptop via cat5 is a pain!

Thanks

Steve
Howdy Steve,

I haven't had time to play with it myself yet, but I believe that you should be able to transcode the stream and either (1) increase the compression ratio [results in somewhat poorer quality] or (2) change compression scheme to mepg4, xvid, or some other newer compression algorithm.  If/when you find a good config, please post your steps here so it can help others!
[INDENT]
   Marc[/INDENT]

---

### Post by SteveGodfrey on 2008-07-07
Can I do any of that with live TV?

---

### Post by ian dobson on 2008-07-07
Hi,

No, transcoding is an offline process, so LiveTV won't work.

As your using DVB you get the stream pre-encoded directly from your provider. If you were using an analog card you can reduce the bandwidth required from within myth-setup.

Regards
Ian Dobson

---

### Post by nasha on 2008-07-07
The other option is to make the move to 802.11n wireless to increase your wireless bandwidth. That is about the only way around your problem...
Although why you would rely on wireless to send a video signal has me baffled. Cables are much more reliable

---

### Post by SteveGodfrey on 2008-07-08
The idea is I use the laptop to watch TV where ever I might be in the house. Could be the kitchen, bedroom etc. I don't have cat5 to those rooms hence the reason for using wireless! I suppose N is an option but then I'd have to replace my WRT54G (running tomato or course)!

I wonder if there's a WRT54G N equivalent.......

Thanks

---

### Post by volkswagner on 2008-07-08
Not sure if this would increase or decrease bandwidth.  Have you tried selecting on the backend "allways stream from backend"?

---

### Post by SteveGodfrey on 2008-07-09
Hey volkswagner

Changing that setting has reduced the bandwidth from 25 Mbps to around 6 Mbps.

Now I can watch live TV over wifi!

Many thanks

Steve

---

### Post by volkswagner on 2008-07-10
Glad you got it posted.would you mind posting details on how you determined bandwidth.

---

### Post by SteveGodfrey on 2008-07-10
I use a simple tool call net-speed. It adds a bandwidth monitor to the gnome bar.  So in this case I started MythtTV then alt-tab back to the desktop and from there I could see how much bandwidth I was using. One tip once you install it go to preferences and set it to display bits per second (bps) and not bytes per second (Bps).

It's brilliant.

Another tool I use for this type of thing is iftop, which works in the bash shell.

---

