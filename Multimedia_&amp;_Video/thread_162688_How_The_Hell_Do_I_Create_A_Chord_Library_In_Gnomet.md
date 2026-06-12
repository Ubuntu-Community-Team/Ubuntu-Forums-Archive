---
title: "How The Hell Do I Create A Chord Library In Gnometab!?"
date: 2006-04-19
forum: Multimedia &amp; Video
---

### Post by Mark76 on 2006-04-19
I can't figure it out :(

---

### Post by Mark76 on 2006-04-19
And why can't I undo when I make a mistake?

---

### Post by BobSongs on 2006-07-03
Excellent question.

I'm working on it. If I succeed... I'll let you know.

---

### Post by BobSongs on 2006-07-04
**How to create a chord library for ****GnomeTab.**
My problem with the application is that when it pops up it's too wide for my 1024 * 768 screen. So I reduced the icons in the toolbar to icons only, no text. (Right-click toolbar, click "Icons Only".)

Once done, I reshaped the application so it looked like a normal app. Then I clicked the fourth icon in the first toolbar that looks like a screwdriver/pliars (the tool tip calls it **Set Gnometab Preferences**). When the box appeared I clicked the **New** button under **Chord Library**.

A box appeared called **Enter New Chord Library Filename**. Here I clicked ***New Folder*** and created one called "GnomeTab"... but feel free to either name yours something else, or just drill your way to some other folder and settle there. Then I double-clicked the GnomeTab folder to open it up. The bottom field had this heading over it:

**Selection: /home/[user]/GnomeTab**

I typed a name into that field like **ChordLibrary**. It doesn't matter what it's called and it doesn't require an "extension" (such as **chords.gtl** for example). Then I clicked OK. That created my GnomeTab chord library file.

**Filling the Library**
Why not carry on with the tutorial, eh? Okay. Let's create a chord for the chord library. First we've got to "expose" the library. If you've reduced your bottom set of icons into "Icons Only" then check out the last icon in the second row. Should look like an empty tab chord with a pencil in it. If it isn't already highlighted... click it. An empty square should appear on the right. If not, don't panic. You may just have to resize the application.

**Adding Chords**
Click the 15th icon (**Build a chord**). Move the cursor and click within the score. The **Create a Chord** box appears. Woot! Let's add **C major**. Click the 5th string, 3rd fret. A flashing caret (cursor) appears. If you're not in the right spot, use the arrow keys to place the cursor at the right spot.

Now click the **3** key either in the numeric keypad or the upper row of number keys. A "3" will appear. Here's the trick!! *Hit the standard Enter key when you're satisfied with its location* *(not the numeric keypad's Enter key)*. The **3** should almost double in size. Now move the cursor up one and to the right one. Hit **2** and Enter. Now go up two and right one. Hit 0 to indicate an open string. Down one, right one, hit **1**, Enter... then up one, right one, hit **0** and Enter. There's our C chord. (If you choose to do this differently or you'd rather work with another chord, be my guest.) If you hit the wrong number followed by Enter and you wish to remove the booboo, middle click the offending digit and it will disappear.

To add the chord to the library click the **Save** icon just under the chord design. Add the chord to the score by clicking the **Create** icon. Or click **Cancel**.

The C chord should now be in the library list on the right. If you don't see it, click the **Select a chord from your library** icon. C should appear on the right. If you *still don't see it,* you may have to resize the application. Again: for me GnomeTab stretches wayyy beyond the right side of the monitor. I have to reshape the application to get it to fit properly.

Once the library is visibile click the C chord. A red rectangle appears around the selected chord. Now click the score and the full C chord appears. Click **Create** and the C chord appears above the staff. 

**The Other Icons**
GnomeTab isn't very intuitive. Other tabbing applications might change what the mouse does depending on where you place it. Not GnomeTab! *sigh* You ***must*** carefully select the icon in the second row to perform various tasks. There's no way around it.

For example. Removing a bad chord. I mean: your score's lookin' pretty except for that little booboo. But how to get rid of it? Click the first icon in the second row (**Select Objects**). Now you can highlight any and everything you don't like. When you do a context menu will appear offering the choice of copying, cutting and deleting.

**Adding the Score**
Well, the howto wouldn't be complete without a bit of a tip here, right? Okie dokie. So. You've got a chord library, right? Big deal. Why can't you add tablature?

Well. Seems the same ... wonderful logic behind GnomeTab rules the tab area too. To add "notes" click the second icon in the second tool bar (should look like a 2 and the tool tip reads: "**Enter numbers or text**"). Now click somewhere in the score. Anywhere really. Now when you type numbers you've got to hit that Enter key *after each entry* or the numbers disappear when you move the cursor. Not exactly what I'm used to in terms of interface. But there you have it.

Now that you're getting a clue as to how this ... interesting ... software works, I'll leave it up to you to determine how the rest of the icons work.

---

### Post by Mark76 on 2006-07-04
Thanks Bob :)

Now, can anyone figure out how to enter text between the staves?  For lyrics.

---

### Post by BobSongs on 2006-07-05
...[this link]("http://solutionm.com/gnometab/gnometab.html").

And [a huge playground of music software]("http://linux-sound.org/one-page.html"). Enjoy.

---

### Post by Mark76 on 2006-07-05
Have you noticed that the rhythm creator bit can't do 8th notes?

Weird.

---

### Post by Mark76 on 2006-07-05
Ah!

Press 8.

---

### Post by Mark76 on 2006-07-05
Why won't Gnometab run now? :cry:

---

### Post by Mark76 on 2006-07-05
I've done everything it said and Gnometab still won't run :( 

Did locking my screen affect it?

---

### Post by Mark76 on 2006-07-05
When I try to run it from the terminal I'm informed that I don't have libatk-bridge.

And neither do the repositories

---

### Post by Mark76 on 2006-07-05
Well, I managed to find libatk-bridge (it wasn't called that) with some help.  Now when I try to run gnometab in the terminal I get

> Bonobo accessibility support initialized
GTK Accessibility Module initialized

I've no idea if this is good or bad.  Either way it's still not running

---

### Post by BobSongs on 2006-07-05
Have you tried uninstalling it, then re-installing?

By the way, this in from the author of GnomeTab:

** Question: **How do you add lyrics to GnomeTab?

[quote="Bill Guelker, GnomeTab author"]

Short answer: you can't.

Longer answer: the addition of lyrics to the tablature was not something that I required, so I didn't do it, nor did I make it easy to add this functionality, unfortunately.

I created Gnometab to fill a need I had at the time as a guitar teacher (and free software geek of sorts).  Since then, I am ashamed to admit that Gnometab has become a neglected project.  I no longer teach guitar lessons, and other work consumes my time these days.

Gnometab was my first significant programming project in C, and I made a number of mistakes -- not so much from a coding standpoint but from a design standpoint.  The Gnometab design is not flexible enough to easily allow different kinds of tablature: bass tab, lyrics, etc..  Fixing these limitations does not require a total re-write, but it is a non-trivial task, and one which I am not able to complete at this time.

If anyone is interested in taking on this work, I will be happy to point them in the right direction.[/quote] 
Don't break your head over it.

---

### Post by Mark76 on 2006-07-06
Yep, I've uninstalled and reinstalled it several times.  It just doesn't want to run :(

---

### Post by shawnrgr on 2006-07-18
> **Mark76 said:**
> Yep, I've uninstalled and reinstalled it several times.  It just doesn't want to run :(

Gnometab is no longer supported by the author, its been almost 3 years since a new release, dump it. Instead use TuxGuitar, far better then gnome tab, lots more features, more advanced, and as an added plus... it can open GuitarPro tabs (*.gp3, *.gp4) so if you use ultimate-guitar.com you can download the guitar pro tabs and open them in TuxGuitar.

A new version was just released yesterday \\:D/ 

[http://sourceforge.net/project/showfiles.php?group_id=155855](http://sourceforge.net/project/showfiles.php?group_id=155855)

---

