---
title: "itunes like app with folder play?"
date: 2011-11-04
forum: Multimedia Software
---

### Post by tomek_wap on 2011-11-04
Hi

Ive searched for an audio player for my 11.04.

Tested: clementine, banshee, amarok, exaile, rhythmbox, listen music player, Guayadeque.

Best ones so far are: listen music player and Guayadeque.

All the rest are so unfriendly.

I am looking for a specific way of adding and playing music to the library –i.e. exactly like it is in iTunes ... seems so simple, yet none of the above meet those requirements.

1. Adding music –importing or drag and dropping FOLDERS to playlist so that it doesn’t split into various ARTISTS (i have many compilations where there are many bands/artists).

This way I can select „folder”/ARTIST from the playlist menu and listen to songs I want, without having to remember or know the artist or song name.

2. Only one of the above apps have a folder listing option which is good, BUT, after clicking on a song to play, when it stops it doesn’t progress to play the next song. One or two more audio players have some way of presenting mp3s in „folder” like manner but also problems arrive when i want to have songs being played one after the other, just like they show up in the FOLDER/playlist view.

Solution to the above seems to be to select with a mouse all the songs in the specific ALBUM to be played (then next songs are played automatically or I can forward to next or previous songs manually) –it’s a pain in the back side to select all songs every time i progress to another ARTIST/ALBUM, especially that i change albums even after 2-4 songs.

I hope the above is pretty clear.

I am looking for an audio player that would do the two simple „tasks”. It seems to me that those two functionalities should be a standard in such players.

Has anyone of you seen an app that would do the above?

Thank you.

---

### Post by nothingspecial on 2011-11-04
Hi,

Not entirely sure I follow you but in the Files tab of Guayadeque you can both drag and drop albums from the right hand "directories" window to the playlist and if you right click and choose play it will play the whole album.

---

### Post by tomek_wap on 2011-11-04
i would prefer not to use playlists.
need to try moving the folder to playlist and see what happenes to songs.

as for the mess in playlists, i will give u an example: lets say i have a The Best of Trance album. almost every song is of different artist (99% of the time we dont remember the artist or the song name) - so how do i/we look for those songs? by selecting The Best of Trance album from FOLDER selection as u at least remember that they are in that album.

and what happens when u import folders into the above mentioned audio players?
it splits those songs into artists in playlist - and imagine you have hundreds or thousands of mp3s ... there's no way u will find those songs. 

thats why itunes works perfectly when it comes to the above matter. but it just doesnt work in wine, at least not on my ubuntu.

---

### Post by aeiah on 2011-11-04
i think the id3 tag 'album artist' is of use here. on compilations, this would be 'Various Artists' but each song would also have an artist tag as well, which would be the actual artist.

its a common problem though, compilation albums. i usually just add a the whole folder to the queue in file browser mode (i use mpd with gmpc, but most music players have a file/folder mode as well as a library mode)

---

### Post by tomek_wap on 2011-11-04
guayadeque seems to work best for me.

in FILES mode/tab i select from the tree an album, press enter and it automatically plays all songs.

which i guess is good enough for me.

thnx for suggestions.

---

### Post by Toz on 2011-11-04
You might also want to give decibel-audio-player a look. Like yourself, I already have my music sorted in folders and don't need the extra level of sorting and categorizing that most music apps do. With decibel-audio-player, I can just drag a folder from my file manager (or from the built-in directory lister) to the playlist and click play. It also comes with remote control capabilities so I can easily assign keyboard shortcuts to control the player and many plugins (covers, now playing exports, etc). Plus its small and lightweight.

EDIT: The oneiric repositories have version 1.06. Version 1.08 is available on their website and fixes a few (annoying to me) bugs and includes a few enhancements. Its python-based so its easy to install.

---

### Post by tomek_wap on 2011-11-04
tried the decibel one, but uninstalled it straight away. didnt like it at all. too simple ;-)

for a second i thought that i'm back to spot one, when i found that in guayadeque there's no SEARCH option in FILES tab ... what a pity ... but that's where i can use LIBRARY tab for searching specific songs.

guayadeque works pretty good :)

---

### Post by tomek_wap on 2011-11-10
does anyone know how to force Guayadeque to load saved layout setting at start up ?
I's very annoying having to close all those useless tabs.

thnx

---

### Post by anonbeat on 2011-11-11
> **tomek_wap said:**
> does anyone know how to force Guayadeque to load saved layout setting at start up ?
I's very annoying having to close all those useless tabs.

thnx

You are having a problem at closing the app. The last used layout is loaded but if the app is crashing when its closing the layout is not saved. What you can do is once you have the layout go to View -> Save Layout and when you want to come to that Layout go to View -> Load Layout.

---

### Post by tomek_wap on 2011-11-11
Crashing? hmmm, it doesnt look like it was crashing, just closing. 

ineed i can load the saved panels, but doing it every time is also a pain in the back side. 

a shortcut like for saving layouts (F4) would do the trick, but it's not there.

still, it is the best player around - at least for my needs.

---

### Post by anonbeat on 2011-11-11
> **tomek_wap said:**
> Crashing? hmmm, it doesnt look like it was crashing, just closing. 

ineed i can load the saved panels, but doing it every time is also a pain in the back side. 

a shortcut like for saving layouts (F4) would do the trick, but it's not there.

still, it is the best player around - at least for my needs.

Maybe you are using an old version. Can you confirm that you are using latest version?
I suggest you to add my ppa 
```
sudo add-apt-repository ppa:anonbeat/guayadeque
```
and add the package guayadeque-svn

If you already had isntalled the package guayadeque you need to remove it first.

---

### Post by tomek_wap on 2011-11-11
i guess i am using latest version as its one from ubuntu software center.

but will double check the packages you mention once ill be back at home, and report back.

thnx.

---

### Post by anonbeat on 2011-11-11
> **tomek_wap said:**
> i guess i am using latest version as its one from ubuntu software center.

but will double check the packages you mention once ill be back at home, and report back.

thnx.

The one from Ubuntu Software Center is quite old. 0.2.7 If I remember correctly when latest official is 0.3.1 and in guayadeque-svn is 0.3.4

---

### Post by tomek_wap on 2011-11-12
Ubuntu'S Software Center contains the latest version, 0.3.1, and this is the one I am running.

Bump ...

---

### Post by tomek_wap on 2011-11-13
Also the equalizer keeps on reseting each time I run the app ...
Something wrong with it  :(

---

### Post by tomek_wap on 2011-11-19
Used Synaptics Manager to completely remove the app.

Installed it again, but it seems to have kept some files, as my saved layout was still available ...

Any solutions pls?

Thnx

---

