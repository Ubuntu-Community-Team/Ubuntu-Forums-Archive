---
title: "NVidia, non-SSE processor, Jaunty, works good!"
date: 2009-04-29
forum: Multimedia Software
---

### Post by lessgov2007 on 2009-04-29
Hello everyone! I just installed Jaunty yesterday and wanted to provide a little information about using an NVidia chipset with an AMD Athlon or other non-SSE processor. I'm using an NVidia GeForce 6200, so anything generally around this model will likely work with this [Beta Driver]("ftp://download.nvidia.com/XFree86/Linux-x86/173.14.15/") that allows for a non-SSE processor. 

I left full [instructions here]("http://lessgov2007.blogspot.com/2009/04/installed-ubuntu-jaunty-jackalope-with.html"). 

Basically all you have to do is add an option to the command line in your GDMSetup. Under Administration choose "Login Window", then click the "Security Tab", then press the "Configure X Server" button. To the right of that dialog you'll see "Command:", and then an input box to the right of that. This is where you have to add your option, but make sure not to erase the commands already there. At the end of the line add "ignoreABI", then close the GDMSetup (Login Window). Hope this helps others...

[IMG]http://4.bp.blogspot.com/_qJjmrMNfViI/SfiE6ARh7II/AAAAAAAAAjQ/IGxJnJpWMkY/s1600-h/Screenshot.png[/IMG]

So far I'm very pleased with Jaunty too. I have an older computer, originally a Windoze 2000 system. Yeah, weak! 384MB Ram, 900MHz processor. Anyways, since Hardy Heron I've had quite a slow down, but with Jaunty the speed has returned, and that makes me a happy camper. :guitar:

I put an image in this post to help others know what I'm talking about, but it wont display for some reason. [If you go here you can see the full thing]("http://lessgov2007.blogspot.com/2009/04/installed-ubuntu-jaunty-jackalope-with.html").

---

### Post by linuxgeek77 on 2009-12-07
Can you please post teh instructions again? i have been trying to make it work with no luck at all. what drivers did you use? the only thing that works is using ubuntu 8.04 with 96.xxx drivers. can you please post the instructions again

---

