---
title: "Fixing the dreaded &quot;white boxes&quot; issue with Beryl Manager - what worked for me"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by foxmajik on 2006-11-08
Hello everyone,

I don't remember how I did it but I somehow ended up with the terrible "white boxes of doom" issue with Beryl yesterday on my Edgy 64 machine.

HOWEVER

I managed to fix the problem by purging all of the Beryl packages AND the XGL X server package, then re-installing them and restarting my X server.

Note that I'd tried it before by uninstalling but not purging and it wasn't fixed, but using the packages to be completely removed then reinstalling them fixed the problem.

I'm actually getting pretty good at reinstalling Beryl and it's misc. components as I experiment with different configurations.

So, to summarize, if your Beryl config gets hosed you can try completely removing these packages:

xserver-xgl -- Mark this one for complete removal and apply.

Then, to remove Beryl, note that beryl and emerald-themes are META packages, which means they install other components for Beryl.

So, to make sure you remove ALL of the components, search for "beryl" in Synaptic and hilite all of the packages with green boxes next to them.  Right click and mark them for complete removal (boy am I glad my mouse has a RIGHT button) and apply.

Now that you've gotten rid of the broken config files, follow this excellent guide on how to install XGL xorg server and Beryl:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

It worked for me, YMMV!

---

### Post by CowzRule on 2006-11-15
Is this what you were getting:
[[IMG]http://i107.photobucket.com/albums/m319/sw54880/th_Screenshot.png[/IMG]](http://i107.photobucket.com/albums/m319/sw54880/Screenshot.png)

---

### Post by foxmajik on 2006-11-17
No, I got a completely white desktop.  I assume this is because Beryl can't get ahold of the compositing extension for whatever reason.

That problem you're having there makes me think you're running low on video memory and your video card is having trouble mapping textures.

Just a guess though.

---

