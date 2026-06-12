---
title: "Songbird, WMA files don't show?"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by doublehard on 2007-06-05
Hi,

I'm new to Ubuntu (4 days and counting) and think that Songbird would be ideal for managing my media library. I've looked at Amorak and Banshee but think that Songbird is the way to go.

My problem is that all my library is in WMA format and in Songbird it doesn't see the files. I've tried to follow the 'howto' [HERE]("http://ubuntuforums.org/showthread.php?t=384644&highlight=songbird") but at the stage "find the file called coreGStreamerSimple.js and drag that to your desktop" I can't do it, every time I try to 'drag it' to my desktop it returns to the window. So I've tried opening it into an editor, all seems fine and I make the recommended "wma" entry then save the file. But everytime I check that it has worked (by reopening it) my WMA addition is missing.

It looks like people have managed to get this working, can anyone give me some pointers.

Thanks very much.

---

### Post by doublehard on 2007-06-06
Sorry to bump, but does anyone have any ideas?

---

### Post by doublehard on 2007-06-07
I've figured out how to do it so here goes:

I followed the following from a thread linked above;

> **GreenDevil said:**
> First, open up a terminal and go to the Songbird chrome directory:


Next, we need to edit a file from the songbird.jar file, so we will need to open that up like so:


Now, open the content folder, followed by the songbird then scripts folder, find the file called coreGStreamerSimple.js and drag that to your desktop, leave archive manager open as we are going to add to it in a moment.

Open it up in your favorite editor, now we are going to add wma support to the "mediaUrlExtensions" section. It should look like this:


Save the file, and drag that back over to the archive manager/songbird.jar file. close it, then fire up songbird and add your favorite wma files!

- GreenDevil

What I had to do differently was extract the coreGStreamerSimple.js file to the desktop, edit it and save it again. Then when I opened it up it showed the alterations were saved. So I then drag'n'dropped it into the archive manager. Then it worked perfectly :p

---

### Post by og.man on 2007-11-09
That is the most locked up file I have ever seen. I can't get it to save. How did you gain permission to edit it?

---

### Post by Catalyst2Death on 2007-11-09
Those instructions weren't clear, I had to fiddle around with it for a while to get it to finally save my edits as well.  I can't remember off hand what I did, but I'm going to reinstall songbird now anyway, and do the same thing.  I'll post my method afterwards.  Sorry I can't be of much help now.  The jist of it is, extract the file to your desktop, edit it, and then reinsert it into the .jar file.  it takes some playing around with, but as soon as I do it again, I'll post instructions

---

### Post by Catalyst2Death on 2007-11-09
Ok, here's what I did, (works for me)

1. open up songbird.jar located in the chrome folder of your Songbird install:
```
cd /(path to songbird install)/Songbird/chrome/
sudo file-roller songbird.jar 
```

this will open up the jar file.  Now you must navigate to the scripts folder (outlined in the other howto) and drag the coreGStreamerSimple.js to the desktop.  Open a new console and type
```
 sudo gedit /home/(usr)/Desktop/coreGStreamerSimple.js 
```

make the edits outlined in the tutorial

save the file.  Now this is the tricky part.  Drag the file back onto the file-roller window.  initially it will look like nothing happened.  you have to move out of the main folder using the back button.  

Then you will see the coreGStreamerSimple.js sitting there waiting to be moved.  

right click and select cut, then navigate back to the scripts folder and paste again using the right click menu.  it will ask you to confirm the path, click ok.

Your finished! now you can start songbird and use your .wma files

Note:  If you installed Songbird from a package or repository, you may not have permission to write to the songbird.jar file. in this case, copy songbird.jar to the desktop, make the above edits, and use
 ```
 sudo cp /home/(usr)/Desktop/songbird.jar /(path to songbird)/Songbird/chrome/songbird.jar 
```

---

### Post by FokkerCharlie on 2008-02-23
Thanks for the guide, works nicely for me.

EDIT:  No it doesn't!!

Initially it worked fine after editing the .js file.  All my albums were discovered and appeared in the library.

After later restarting, however, the albums had disappeared, and weren't discovered on a subsequent scan.  I have checked that "wma" is still included in the script (it is), deleted and reloaded Songbird, to no avail.

Can anyone help debug this?

Charlie

---

### Post by FokkerCharlie on 2008-02-24
OK, I've fixed this.

Had to delete the folder I'd put songbird in, then remove -/.songbird1 and start again.

Charlie

---

