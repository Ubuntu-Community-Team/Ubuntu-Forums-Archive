---
title: "anything like muvee available for linux?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by bonzini on 2007-05-14
Hello good people;

Back when I was silly enough to be running XP on my laptop, one of the very cool things that I used from time to time was a piece of software called "Muvee" - in my case, it was in fact a kind of plug-in version in the Nikon software that came with a camera I purchased.

What Muvee did/does, or at least what I used it for anyway, was to automatically animate a sequence of images (interesting fades, wipes, dissolves, pans, merges, etc) and merge in a sound track.  If you haven't seen it work, you may think this is hokey - ok if you HAVE seen it work you may think it's hokey too, but I liked it.  And, I suppose, the most interesting thing was what a great animation you got just by clicking on "do it".  I suppose there are many "pro" options but the default styles included in the plug-in version were quite acceptable for my purposes.

Does anyone know if there's a similar capability available for Linux?  The only two things I see on the Ubuntu forums are people noting in passing that one of the reasons they keep their 'doze partition around is to use Muvee...

Thanks in advance!

---

### Post by Statik on 2007-05-14
Well, if you mean "are there programs that allow me to do the same things as muvee allowed, but not necessarily in the same way" then yes. Cinelerra is a NLE (Non-Linear-Editor) that seems to work fairly well. I've had some issues with it not doing transitions as expected, but it works well for stringing photos and such together and then adding transitions and audio. My preferred application for this is Blender. Blender has a sequencer in it that allows me to do all of the things Cinelerra allowed, but with smoother transitions and more control. It isn't as easy to learn tho, and it isn't as automated. What do I mean by that? Well, say I wanted to cross-fade between two film clips. I can add both to the sequencer, overlapping them, and add a cross-fade transition, and it will cross-fade them in the time-span they are overlapped. Easy, yes? What about the audio? Here I have to add 'nodes' to an IPO curve and have the volume of one decrease for that same time period, and then the volume of the other increase for that same period. It doesn't automatically have to be the same time period. Much more tweakable, but less newbie friendly. However, in my book, it is somewhat easier than Cinelerra because it seems to work reliably and predictably.

Statik

---

