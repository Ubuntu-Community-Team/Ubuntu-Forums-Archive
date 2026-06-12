---
title: "Can't choose file order on CD burning"
date: 2010-03-18
forum: Multimedia Software
---

### Post by aj_the_first on 2010-03-18
Okay, all I want to do is this: choose the order (other than alphabetical) of the files that I burn to a disc.
Brasero doesn't allow it
K3b doesn't allow it
GnomeBaker doesn't allow it

Unless I am missing something, I can't figure out any way other than renaming all my files with a single number and/or letter at the beginning of a file name to choose the order of files.  This blows my mind it seems like the most "no duh" feature that everyone would need in any Cd burning program.
Please tell me if I am stupid or if the software developers are stupid. (because I really can't see any other options)

This is seriously so important (to me), that I will abandon Linux and go back to Windows if I can't do it.

Thanks

---

### Post by ron999 on 2010-03-18
Hi
If you're making an audio cd then k3b _does_ allow you to decide the order of the tracks. Add them one at a time in the required order.

---

### Post by alegallo on 2010-03-18
I don't think it's about audio cds, and I must say I had the same problems burning a cd with several divx files for my child.
I did just the same as you thought: I renamed all of the files starting from 01 to about 15, and it worked.

On the other hand, I don't remember any win app that puts the files on a cd other than in alphabetical order, right? ;)
At least Nero and win cd burner don't

---

### Post by Yellow Pasque on 2010-03-18
I like xfburn. It lets you order your tracks by dragging the files around.

---

### Post by aj_the_first on 2010-03-18
xfburn, I'll give that a try. thanks.

I heard that I can drop them in the order I want on K3b, so I tried that, but it still put them in alphabetical order as I dropped them, and then when I burned them they were in a totally random order.  This is true of Brasero and GnomeBaker: regardless of the order it shows in the window, the files will be burned in a totally random order.
And I know I can rename my files with numbers at the beginning to get the order I want, but I just feel that I shouldn't have to "trick" the software into doing what I want it to do...  If I wanted to do that, then I would have bought a Mac...  ;)

I don't know what I used in Windows, but it was a default program (on my Toshiba at least), and I could just drag and drop stuff into the window, and then continue to drag and drop them inside the window until I liked the order, and then click burn.  Too easy.

Now don't get me wrong, I hate Windows in soooo many other way, and I have been faithfully using Ubuntu for about a year now, but I just recently needed to start burning CDs with multiple files again, and found this problem.  If I was still skilled at programming (haven't done it in about 8 years) then I would try to fix it, but I'm not that guy anymore...

Thanks again for your help.

---

### Post by aj_the_first on 2010-03-18
Nope... doesn't work in xfburn either.  It keeps them in alphabetical order...

---

### Post by sebastianabate on 2010-03-18
But not matter in what order the files are added in the burning program, once burned, the resulting cd shows the files in the order according to the viewer program's settings (named nautilus, explorer, konqueror, bash, etc.)
Why are you trying to set the order at the burning stage? Do you need it for a special program in the CD?

Note: we are talking about data CD, right? Because at least with brasero you can sort the audio tracks manually.

Note2: Nero for Linux have the option "Do not sort" in the "View -> Arrange icons by" menu, but again, the files are going to show in the order according to the viewer program's settings.

---

### Post by aj_the_first on 2010-03-18
Ah, I should clarify.  I am burning music, but as a data disc because if you choose audio disc you can only fit about 20 songs or less.  If I burn mp3s in a data disc format then I can burn about 100+ songs.  My CD player plays the mp3 data format discs, and this is where I find out the random order.

---

### Post by sebastianabate on 2010-03-18
OK, now I understand. _[Try the Nero 4 trial]("http://www.nero.com/enu/downloads-linux4-trial.php")_, I don't know if the "do not sort" option are going to work for you, but worth a try.

Edit: The forum search tool is a good thing!!!! _[This is a thread]("http://ubuntuforums.org/showpost.php?p=7503949")_ about your problem, with a couple of solutions _([this one looks good]("http://ubuntuforums.org/showpost.php?p=7503949&postcount=7")_)

---

### Post by ricardisimo on 2010-04-18
Somewhat related issue I'm having with k3b...

Suppose you are making an audio CD, we'll call it a Radiohead mix for our purposes here. You select your favorite 15 or so songs, but just before you are ready to burn, you decide that "Everything in Its Right Place" absolutely has to be first, and "4 Minute Warning" should go last. That should be clear to everyone, right? ;)

So you grab one of them from wherever it is in the list, and drag it to where you want it. First problem: you now have two instances of the song in your list - the one in its original slot, and the one in its new slot. Second problem: if you linger even just a little with the track as you are moving it around in the list, k3b appends it to another song, rather than dropping it into the next slot. In other words, rather than dropping it into slot 7, it appends it to whatever song is at number 6. That's a problem, especially given that k3b does not have "Edit... Undo" options in its menu.

I suppose the solution is to use Brasero, but I loathe this program, not only for the fact that its "sane defaults" take 45 minutes to burn a regular audio CD, but also for its lack of any truly sane options anywhere in its menus.

I thank you for any ideas with how to make k3b work better for me.

---

