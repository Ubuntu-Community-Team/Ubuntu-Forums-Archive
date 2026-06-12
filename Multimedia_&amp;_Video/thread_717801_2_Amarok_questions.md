---
title: "2 Amarok questions"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by bobbo85 on 2008-03-07
1) 
I am new to Amarok and was wondering how I can show the contents of my ipod in the playlist window.

I have used itunes in the past, and I could click on the ipod icon to the left sidebar, and I would see all of the songs show up in the main window.
The same goes for Rhythmbox.

Essentially I like being able to see a list of all songs in any playlist or device, so I can add and remove songs easily.

2)
How can I delete (physically) the currently playing song?  I currently have hundreds of songs that a friend gave me, so I have the songs playing and would like to be able to be like "ok i don't like this song" and hit like Ctrl+alt+D or something.  For bonus points, is there a way to remove the playing song with the mouse?  Like right click somewhere in the player, and select "delete current song."  That would be great if I'm across the room with a wireless mouse doing homework or something.

3) (Added after I made the post title..)
How can I make the playlist go to the currently playing song?  Or at least make it easy to see in the list by highlighting it or putting an arrow next it or something.  I know I can see the title of the song in the window titlebar, and I could then search for it in the playlist window, but there has to be an easier way to locate the current song.

Thanks in advance everyone!

PS:  I have been dual booting Ubuntu and XP for about a month now, and I just realized I've only used windows for about 20 minutes since then :-)  I just yesterday resized my partitions too, looks like Linux for the win!

---

### Post by jpoRS on 2008-03-13
I don't have a full answer for all the questions, but hopefully I can help.

1.) You can find your iPod under the "Devices" tab on the left of the window. If I remember correctly there is a drop down menu at the top, select "iPod", then click connect (It looks like a plug with a lightning bolt), and it should connect then.

I don't remember if this is all you have to do, I set up my Zen a while ago, and I don't even know how different a Zen would be from an iPod.

2.)Left click the song>Manage File>Delete File

I had some trouble with this.  When the screen coming up asking to verify that you want to delete the song, I had to select to permanently delete the song instead of just sending it to the trash.  I don't know if its because I am using it in Gnome or what, but it gets rid of songs!

3.)The currently playing song should have a big bubble-like thing on it.  I don't really know how to describe it, but its kinda like the song gets highlighted with a magnifying glass?

Hope this helps!
Peace
jim

---

### Post by bobbo85 on 2008-03-27
My solution to the delete current song question:

I found this site [http://ubuntuswitch.blogspot.com/2007/12/delete-songs-amarok-script.html](http://ubuntuswitch.blogspot.com/2007/12/delete-songs-amarok-script.html)

It contains the code for a script that will move the currently playing song...

The run down of what I did:
1)  Make a folder for your "trash songs"
2)  Make a script with a text editor to move the current playing song to that folder
3)  Set a global keyboard shortcut to run that script

Here are the actual steps (Hope they are easy and correct!  They worked for me)

1)  Make a new file called something like "delsong.sh"
2)  In a text editor, copy and paste the following code into the new file:
```
#!/bin/bash
path=`dcop amarok player path`;
s1=`basename "$path"`;
mv "$path" '/home/bob/mytrash/'"$s1";
```
NOTE:  
You can change the last line to match the directory you created for your "deleted" songs.
You can also change the last line to just delete the songs by using "rm" instead of "mv" - and in this case you don't need the new file location.

3)  Set the permissions for that new script file to executable (either by right clicking and going to "permissions" and checking the box, or by using the chmod command in the terminal.
4)  Open up the gconf editor (run gconf-editor) and navigate to apps->metacity->keybinding_commands
5)  Edit one of the commands there (I used command 1), set the value to the location of your script file (ex:  /home/bob/delsong.sh)
6)  Navigate to global_keybindings (it's also under metacity)
7)  Edit the command you chose in step 5.  Set the value to the key combo you want (I used <CONTROL><SHIFT><D>)

Done:-)  Try playing a song in Amarok and using your new key combo.  On my computer, I have to wait until the song has finished playing, but it does indeed move the file for me.

Best of luck!

---

