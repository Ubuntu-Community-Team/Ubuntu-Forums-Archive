---
title: "Overheating CPU killed Banshee"
date: 2018-08-03
forum: Multimedia Software
---

### Post by paulakreuzer on 2018-08-03
Yesterday at 15:11 my computer crashed. GNOME Logs has pages full of CPU overheating logs, but I was never warned.
Since then banshee - which I had used at that time among other apps - doesn't work anymore.
I can open the app, browse my library, search for a song & even play a song, but once the song finished playing the app crashes.
The app also crashes immediately if I: click on a playlist, click on the play queue, edit a song, rescan the library and sometimes during other processes.

The only message I ever saw during one of such crashes was the first time I finished playing a song. This message appeared:

  	 	 	 	   ```
An unhandled exception was thrown: Value was either too large or too small for an Int32.

 
 
   at (wrapper managed-to-native) Gtk.Application:gtk_main ()

   at Gtk.Application.Run () [0x00000] in <7a41aae9f05e45b7b5a8cedfab67f8ff>:0  

   at Banshee.Gui.GtkBaseClient.Run () [0x0001e] in <b99441556f0248258aff30b6707b44a0>:0  
   at Banshee.Gui.GtkBaseClient.Startup () [0x0000b] in <b99441556f0248258aff30b6707b44a0>:0  

   at Hyena.Gui.CleanRoomStartup.Startup (Hyena.GuiCleanRoomStartup+StartupInvocationHandler startup) [0x0004f] in <2339076111b44174acb3706ba9bf4e2b>:0  

 
 
 .NET Version: 4.0.30319.42000

 OS Version: Unix 4.15.0.29


```  

The first log about banshee is from yesterday at 14:16 and it says:

```
[session uid=1000 pid=1461] Activating service name='org.gnome.GConf' requested by ':1.79' (uid=1000 pid=2057 comm="banshee /usr/lib/banshee/Banshee.exe --redirect-lo" label="unconfined")
```

I have many more logs which I don't understand, but if anyone can make anything out of these I'll gladly post more.


What I tried so far:
[LIST]
[*]Reinstalling banshee
[*]clearing system cache
[*]I noticed once that when I started banshee it tried to save metadata to a file, so I disabled that function and deleted the last files I had played
[/LIST]
Nothing changed.

Does anybody have an idea what I could try?

---

### Post by Holger_Gehrke on 2018-08-03
I haven't used banshee in a long time, but I do recall that it's recovery from crashes is basically non-existent. It uses some kind of embedded database (sqlite? msql ?) for storing statistics and metadata and those files get easily corrupted when the system crashes while they are in use. There should be a hidden directory full of files related to banshee in your home directory, either '~/.banshee' or '~/.config/banshee' IIRC. Renaming this directory (while banshee is not running) to 'banshee-old' should reset banshee to a freshly installed state. You'll lose settings, any metadata not stored in the music files themselves and possibly your playlists, but banshee should work again. If you're feeling adventurous, you can try to restore some of the stuff from the old banshee folder to regain what got lost or if getting it working again is all you care about, you can erase that folder.

Holger

---

### Post by paulakreuzer on 2018-08-03
Thanks for your reply.

You are right. Renaming/removing the banshee folder gets banshee working again, but it's empty. Putting the folder back in place returns banshee to the previous crashing state.
Only the banshee.db file seems relevant though.

Unfortunately saving my database with metadata, plays and ratings is more important to me than using banshee, so I guess I'll hope for a good tip in the other topic:
[https://ubuntuforums.org/showthread.php?t=2397776](https://ubuntuforums.org/showthread.php?t=2397776)

---

### Post by Holger_Gehrke on 2018-08-03
Perhaps this article can help you: [https://thelinuxexperiment.com/recovering-a-corrupted-banshee-database/](https://thelinuxexperiment.com/recovering-a-corrupted-banshee-database/)

Edit: Also, the player I use (clementine) semi-regularly makes a backup of its database in '~/.config/Clementine/clementine.db.bak'. Perhaps banshee does something similar ?

Holger

---

### Post by paulakreuzer on 2018-08-03
Thanks. I found another article which basically provides the same tips (integrity check+reindexing and dumping): [https://www.techyv.com/questions/banshee-encounters-fatal-error-launch/](https://www.techyv.com/questions/banshee-encounters-fatal-error-launch/)
Both change nothing. And the strange thing: The integrity check comes back with no errors, it just prints out "ok".

So now I'm thinking it might not be the database after all.
When I remove the banshee config folder and start banshee a new folder appears with a log file that is already full of error messages.

So I tried to purge banshee and reinstall, but still no change.

The error messages in banshee's log file look a lot like the ones posted here:

[https://askubuntu.com/questions/1029925/banshee-crash-when-adding-folders-to-the-library](https://askubuntu.com/questions/1029925/banshee-crash-when-adding-folders-to-the-library)

---

### Post by paulakreuzer on 2018-08-05
I don't want to jinx it, but I think I just fixed it (If you don't hear back from me that means I did ;) ).

What struck me as odd was that banshee always crashed immediately when I clicked on any playlist.
So what I did was open the banshee.db file with "DB Browser for SQLite" and removed all records in CoreSmartPlaylistEntries and CorePlaylistEntries.

I had to reload every smart playlist, but now everything seems work again without any data lost.

Thanks a lot @Holger_Gehrke for helping me get there. :) [[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")

---

