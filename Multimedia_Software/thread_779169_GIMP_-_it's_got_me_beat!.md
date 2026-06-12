---
title: "GIMP - it's got me beat!"
date: 2008-05-02
forum: Multimedia Software
---

### Post by svaens on 2008-05-02
Damn Gimp. 
I know that is not the best way to start a thread, when there are probably lots of people out there that like the tool. But damn! I am not that stupid, but i can't work the bloody thing out. 

All I want to do is use the clone tool, and clone a piece of image onto another part of the same image. 

I'm not working with more than one layer, and i shouldn't have any transparencies (that I know of) ... 

So I Ctrl-MouseClick my source, and the circle appears there... 

I move my mouse to the destination, and go to paint ..... 

But nothing happens.... the clone circle moves around, and so does the circle where my mouse is..... but nothing is being painted. 

I am probably doing something wrong. But geez!!! Why does it have to be so complicated then! I have used other tools like paint shop pro... and it is instantly usable ... because it is intuitive. i NEVER needed to read any manual or istructions or watch you tube tutorials to work out how to use the clone tool... .. 
and i've done all of the above just now for GIMP, and I still can't get it to work. 

damn!

Help!

---

### Post by cor2y on 2008-05-02
The first time i used Gimp i hated it too.
The same thing for Adobe Photo Shop and Fireworks.
But visiting the right sites and continued use got me accumulated to Gimp.
Now creating wallpapers and editing pics are a cinch.
This is where i went for tutorials  etc. believe much better than the Gimp help file/html page.
[http://www.gimptalk.com/](http://www.gimptalk.com/)

---

### Post by svaens on 2008-05-02
Thanks! I'll give it a good read!

---

### Post by dougfractal on 2008-05-02
pixel2life is a great tutorial site

[http://www.pixel2life.com/tutorials/Gimp/All/](http://www.pixel2life.com/tutorials/Gimp/All/)


Did you set the source position first Ctrl+click

---

### Post by WinterWeaver on 2008-05-02
Clone tool works perfectly for me... are you sure your your clone brush is using the full pressure?

Check the Pressure sensitivity  etc... play with the settings.

there is no trick and you dont need any manuals. ^_^

---

### Post by WinterWeaver on 2008-05-02
Decided to give you screenies ^_^

first, check your brush settings, then check on the layers panel, make sure you dont have the lock transparency button selected.

---

### Post by Cannaregio on 2008-05-02
> **svaens said:**
> Damn Gimp. 
I know that is not the best way to start a thread, when there are probably lots of people out there that like the tool. But damn! I am not that stupid, but i can't work the bloody thing out. 

All I want to do is use the clone tool, and clone a piece of image onto another part of the same image. 

I'm not working with more than one layer, and i shouldn't have any transparencies (that I know of) ... 

So I Ctrl-MouseClick my source, and the circle appears there... 

I move my mouse to the destination, and go to paint ..... 

But nothing happens.... the clone circle moves around, and so does the circle where my mouse is..... but nothing is being painted. 

I am probably doing something wrong. But geez!!! Why does it have to be so complicated then! I have used other tools like paint shop pro... and it is instantly usable ... because it is intuitive. i NEVER needed to read any manual or istructions or watch you tube tutorials to work out how to use the clone tool... .. 
and i've done all of the above just now for GIMP, and I still can't get it to work. 

damn!

Help!


Verbatim from Apress' Gimp Novice -> Professional:

[I]The Clone tool lets you duplicate a small area over and over, to paint an object out of a picture.
    [COLOR="Blue"]The first time you try to use it, you&#8217;ll probably be frustrated. You click and drag, expecting patterns from nearby areas to be copied&#8212;just like with Smudge, only smarter. But nothing happens![/COLOR] The cursor shows a crossed-circle saying &#8220;No&#8221;! Why won&#8217;t it let you paint?
The key to the Clone tool is first selecting the region you want to clone by holding down the Control key while clicking. Once you&#8217;ve selected the region, you can duplicate it over and over by dragging, painting just as if you were using the Paintbrush tool.
     This is much more powerful than simply dragging whatever is nearby, like Smudge. You can even Control-click in one image, and then drag in another, cloning parts of the first image into the second.
     But there&#8217;s one other trick to using the Clone tool: it doesn&#8217;t restrict itself to the pattern that was inside the brush outline when you Control-clicked. If you keep dragging, it will continue copying from the source image. This means the direction and length of your drag is very
important.
     For that reason, choose a large source region if you can (though it&#8217;s not always possible), and use fairly short strokes. Be careful not to drag too far.
     Also, if you&#8217;re trying to paint a specific object out of the picture, use direction to your advantage.
     As with most touch-up techniques, a fuzzy brush usually works best, unless you&#8217;re cloning near a sharp boundary like the edge of a rock or tree trunk against the sky.
    Change the source region whenever you need to. You&#8217;ll probably need to grab from several different source areas.
[/I]

---

### Post by Katerine on 2009-12-31
This is an old topic, but I just had the same problem last night, and realized the solution this morning, and thought it should be documented somewhere for Googling purposes.

In my case, the problem was that I was trying to clone out a phone line that was running along the entire bottom portion of the image - from the left side to the right side. "Naturally," I thought, "I will select the sky right above the phone line, on the very left edge of the photo, and clone from the very left edge of the photo to the right." So that's what I did. And nothing happened. Even though, according to the Undo menu, GIMP was under the impression that it had just cloned.

The problem, as I confirmed this morning, occurs when either the clone source or the starting point of the clone-destination area overlaps, even slightly, with the edge of the photograph. I'm guessing because GIMP considers anything beyond the edge of the photo to be transparent, and this somehow overrides even the non-transparent areas.

The solution is to set the clone source and the starting point of the destination to someplace a little ways into the photo, to make sure that nothing overlaps the edge. And then, if you need to clone to the very edge, start at the inside end, and shift-clone backwards, setting the end point out beyond the edge of the photo.

Anyway, that was the problem and the solution in my case. Hope that helps somebody. :)

---

