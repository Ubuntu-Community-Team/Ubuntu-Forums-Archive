---
title: "Copy playlist tracks and Rename according to track order."
date: 2010-10-02
forum: Multimedia Software
---

### Post by aadam12 on 2010-10-02
I'm currently running Meerkat beta AMD64.
I've been using Audacious in Ubuntu for years, before that I used XMMS.  

In Windoze I used to use Winamp.  Winamp has a plugin called gen_yar.  Gen_yar would allow you to right-click on the playlist and copy your current playlist files in track  order to any folder on your hard drive, or to a USB mounted mp3 player/thumb drive, whatever.

It had  several checkboxes in the settings. 
1) Rename the files adding the track  number as the prefix (01_, 02_,  etc). 
2) Create a .m3u playlist of the tracks in that  new  folder using #EXTINF: instead of the full path. That way I can copy that  folder to any gadget or another computer and the playlist will still  play those files.

Here is the Winamp Plugin: gen_yar (Yar-matey!_Playlist_Copier)
[http://www.bcheck.net/apps/gen_yar.htm](http://www.bcheck.net/apps/gen_yar.htm)
There's a link to the source code at the bottom of that site if that helps.

Here's another: 
Winamp Plugin Save Playlist In Order
[http://www.winamp.com/plugin/save-playlist-in-order-to-mp3-player-v4/221680](http://www.winamp.com/plugin/save-playlist-in-order-to-mp3-player-v4/221680)

I have yet to see this feature in any Linux media software. I've tried just about all of them. The only  thing close would be drag-n-drop playlist files from Rhythmbox.

Does anybody know of a plugin for Audacious or Rhythmbox that will do this?

Alternatively,  is there a Nautilus script that when I right click on a folder full of  mp3s, it will create a playlist of files in that folder, and save that  playlist file inside the folder (without the full paths as mentioned  above)?

I hate having to boot into Virtual Box just to use Winamp to create portable playlists.

Unfortunately, I am not a developer or script writer so your help will be greatly appreciated.

---

### Post by aadam12 on 2010-10-02
Sorry to reply to my own post but I was just reading about .m3u files 

An M3U file is a [plain text]("http://en.wikipedia.org/wiki/Plain_text")  file that specifies the locations of one or more media files that the  media player should play. Each line carries one specification. The  specification can be one of:
 
[LIST]
[*]an absolute local pathname e.g., C:\My Music\Heavysets.mp3
[*]a local pathname relative to the M3U file location e.g. Heavysets.mp3
[*]a URL.
[/LIST]
 The M3U file can also include comments, prefaced by the "#" character. In **extended M3U**, "#" also introduces extended M3U directives.

Wikipedia [http://en.wikipedia.org/wiki/M3U](http://en.wikipedia.org/wiki/M3U)

So this task sounds a bit easier. I need a plugin or script to do the following: 
1) copy the playlist files to a new folder
2) rename them in track order
3) create a simple list of the files in that folder and save it (in that same folder) as text with the extension .m3u
(see above: a local pathname relative to the M3U file location e.g. Heavysets.mp3)
No need for the #EXTINF:

Thanks again.

---

### Post by mapman88 on 2010-10-03
Hi aadam12, "In a related story", I am using Guayadeque music player. I ripped some music cd's using RipperX, using Lame to encode them to mp3 files, and a m3u file was created in each folder of each album I ripped to my music folder. When I scanned all the ripped cd's to my Guayadeque Library, it only brought in nine tracks from each album, even though in some albums there are obviously more tracks than nine. I posted a question and was reading posts when I saw yours, and recognized the reference to m3u files. If I open my m3u file with open office word (Amy Winehouse - Black to Black) there are only nine tracks listed in the file. Even though there are eleven tracks on the album, and RipperX ripped all eleven tracks to the Amy Winehouse- Black to Black folder. So even thoughI have all my tracks in Guayadeque, they cannot be sorted by album. In the Amy Winehouse example, One through nine are together and ten and eleven don't have a track number or an album name to sort them with the other Amy tracks. I think I need a script to add the tracks above nine to the m3u file, which Guayadeque must use when it scans everything into the Library. Anyways....., I'll keep an eye on your post.

---

### Post by aadam12 on 2010-10-03
Thanks mapman88. I thought Guayadeque was a pretty new project? Did you already let them know about this bug? If not, here's their link [http://sourceforge.net/projects/guayadeque/](http://sourceforge.net/projects/guayadeque/)

I see that Guayadeque will export the tracks to any directory but it won't append the playlist track number to the filename as a prefix. It also created m3u files but they have the full path to the original file. All I need is the filename without the path.

---

### Post by aadam12 on 2010-10-03
[SIZE=2]Sorry to keep updating my own post but I found this Nautilus Script which helps.

[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]**Script-m3u - **[/FONT][/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Times New Roman][FONT=arial][SIZE=2]This script allows you to create a playlist.m3u of mp3 files contained in a folder (without the paths)[/SIZE]
[/FONT][/FONT][/COLOR][http://gtk-apps.org/content/show.php/Script-m3u?content=129888](http://gtk-apps.org/content/show.php/Script-m3u?content=129888)

You could also do a simple command 
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]ls *.mp3 >> Playlist.m3u[/FONT][/FONT][/COLOR]

---

### Post by aadam12 on 2010-10-03
I found a better script 

[COLOR=#000000][FONT=Times New Roman][COLOR=#9E9E9E][FONT=Verdana][B][SIZE=3]m3u-playlister[/SIZE]
[/B]

[/FONT][/COLOR][/FONT][/COLOR][http://linux.softpedia.com/progDownload/m3u-playlister-Download-53177.html](http://linux.softpedia.com/progDownload/m3u-playlister-Download-53177.html)

---

### Post by mapman88 on 2010-10-03
Hey aadam12,

I am thinking of running the [COLOR=#000000]ls *.mp3 >> Playlist.m3u. Do I need to point it at my music folder in terminal somehow, or do I just open a terminal, type it in and go? I am not very knowledgeable using terminal.

thanks,


[/COLOR]

---

### Post by aadam12 on 2010-10-03
Open terminal
cd ./Music/YourFolder  (or wherever you music is stored)
[COLOR=#000000]ls *.mp3 >> Playlist.m3u 
(you can name it anything. Doesn't have to be Playlist.m3u)

It works immediately. Open YourFolder and you ill see Playlist.m3u
If you open that in gedit text editor you will see that it created a list of the .mp3 files in that folder.
[/COLOR]

---

