---
title: "GNUMP3d and live broadcasting"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by ROUBOS on 2007-08-18
Hi all,
I've been searching online for information and software that can easily setup a radio broadcast over the internet. My friend has a local radio station and I have installed feisty on his machine. I have come across GNUMP3d and it seems like a simple way to broadcast music online.

I was wondering if anyone has used GNUMP3d before and knows if it allows you to stream from the mic.

or

if anyone can suggest another way to broadcast from the mic live, and just have a link to a website for listeners to access the live stream


thanks people

---

### Post by freeflyer57 on 2007-08-18
I used GNUMP3d for a long time. All it does is puts folders that you specify accessible to the world. So if you wanted to do mic stuff, then it would have to be recorded and then put into that folder.

---

### Post by ROUBOS on 2007-08-18
ok cool
that does not help then as I need to stream from the mic live.

---

### Post by freeflyer57 on 2007-08-18
Did you try looking through the amatuer radio section of synaptic?

---

### Post by freeflyer57 on 2007-08-18
nevermind thats for ham radios.

---

### Post by freeflyer57 on 2007-08-18
There is internet Dj console ([http://idjc.sourceforge.net/]("http://idjc.sourceforge.net/"))
 
I have no personal experience with this application though. But it looks very professional. Hope that helped.

Also, it's in synaptic. search for idjc.

---

### Post by ROUBOS on 2007-08-18
thansk for that. will look into it :)

---

### Post by freeflyer57 on 2007-08-18
You'll have to leave me a meassage if you get your radio working so i can listen! :popcorn:

---

### Post by mohnkern on 2007-08-20
What you really need are two components, a server component, and then a DJ component.

For a server, Shoutcast, while not part of the Ubuntu distribution, is extremely easy to install, it's available at [http://www.shoutcast.com/download/serve.phtml](http://www.shoutcast.com/download/serve.phtml) .

This server basically takes in an audio feed, and sets it up so people can "tune in" to it.

Then you'll need a DJ application.  IJDC is new (mentioned above) and looks good, but I haven't tested it yet.

Honestly, discussion has indicated there isn't a pro quality DJ application for Linux out there.  "Industry standard" is Spacial Audio's Sam Broadcaster.  ([http://www.spacialaudio.com](http://www.spacialaudio.com)) but its only in Windows.

You could set up a VM and run Broadcaster in it.  However normally, for a Broadcasting server, you want to minimize the # of other applications your running to make it efficient.

---

