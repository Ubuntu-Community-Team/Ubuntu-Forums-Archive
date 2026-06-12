---
title: "Reconfigure Rhythmbox to use single library location?"
date: 2010-05-12
forum: Multimedia Software
---

### Post by sorenmogensen on 2010-05-12
Have a problem with Rhythmbox (under 64bit Lucid) - 

I copy all music to a single location (~/music) which makes it easier to backup and manage. However, Rhythmbox looks for music both here, and under the purchased music folder, which means that any music I have purchased gets listed twice - once from my music folder, and once from the purchased music folder.

I have tried using gconf-editor to change apps/rhythmbox/library_locations to only include my music folder, however when next I restart Rhythmbox, the setting reverts to also including the purchased music folder.

Is there a way of preventing this from happening?

I only want "~/music" listed for library locations - I do not wish to include "~/.local/share/ubuntuone/Purchased%20from%20Ubuntu%20One".

---

### Post by mercury80 on 2011-01-12
I got the same problem. I messed up playing with the settings... and now Rhythmbox is watching way to many folders!!!

---

### Post by armyofgayunicorns on 2011-01-12
Had similar problems with Rhythmbox, also found it annoying that when all my music is on a seperate hardrive it takes ages rescanning and rebuilding the library every time I started it up. I've just started using Banshee instead and I've had no problems at all with it, best media library management I've yet seen in any music player app, very easy to fix incomplete or wrong metadata, unknown artist problems etc.

---

### Post by TaffyDownUnder on 2011-03-05
I have same issue. I copy all my music on to a NAS and I don't want Rythmbox to include the purchased directory in its search for music files.

It is very annoying.

---

### Post by mercury80 on 2011-03-06
I managed to fix my problem. But I was trying so many different things at the same time that i can't be sure what did the trick. I uninstalled Rhythmbox and deleted just about everything I could find of Rhythmbox in the home-folder. Like ~/.local/share/rhythmbox and ~./gconf/apps/rhythmbox. Then installed Rhythmbox again.

Approximately...

---

### Post by d.vanheeckeren on 2011-03-29
what worked for me...

```
sudo su root
<password>
apt-get purge rhythmbox
apt-get install rhythmbox
exit

```

---

### Post by aqualad on 2012-01-11
Sorry to revive an old thread, but google brought me here. I'm really surprised nobody posted any fixes.

**_Here's a simple way to change your library location and which folders are being watched_**:

Through the terminal:
```
cd ~/.gconf/apps/rhythmbox/
```
Open the config file with a text editor
```
gedit %gconf.xml
```
Remove any list items you don't want included in your library, be sure to remove all three lines for each folder you remove. 
```
<li type="string">
[INDENT]<stringvalue>file:///the/directory/being/removed</stringvalue>[/INDENT]
</li>
```Save and close, that's it, your list of library folders will only include Ubuntu One downloads next time you launch.

Note: If you remove the Ubuntu One entry, rhythmbox will replace it automatically.






sorenmogensen (OP): I don't see a simple, proper solution. I didn't test it, but I think you could make a simple workaround by deleting ```
~/.ubuntuone/Purchased\ from\ Ubuntu\ One
``` Then create a symbolic link to your preferred music folder (don't forget the Unix is CASE SENSITIVE and that ~/music is different from ~/Music).  ```
cd ~/.ubuntuone/Purchased\ from\ Ubuntu\ One && ln -s ~/music Purchased\ from\ Ubuntu\ One
```  Last, you would have to change which folder(s) rhythmbox watches to the new symbolic link in rhythmbox by doing: edit > preferences > Music.  Set it to the directory above ```
~/.ubuntuone/Purchased\ from\ Ubuntu\ One
``` 

Side Effect: Ubuntu One downloads would go directly into your music folder.

---

### Post by Mujaheiden on 2012-12-27
All locations have changed, the today working solutino is at comment #6 at
[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/112192](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/112192)

---

### Post by howefield on 2012-12-27
Old thread closed.

---

