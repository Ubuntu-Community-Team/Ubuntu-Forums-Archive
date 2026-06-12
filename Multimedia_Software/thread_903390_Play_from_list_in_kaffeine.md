---
title: "Play from list in kaffeine"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Rany Albeg on 2008-08-28
Hi,

Lets say i've created a list contains all songs from a certain directory which their names starts with the character "0" for example ,using the cmd:

'touch playlist;( ls|grep "^0" . )>playlist'

and now i want , using a bash script , to play them all one by one like a simple playlist.

Is there any way to do that?
Or simpler: how does the 'while' loop works in this case.
I'm working a lot with c++ so the syntax is my main problem.

Any help will be appreciated.

Have a nice day ;)

---

### Post by Rany Albeg on 2008-08-29
I saw that there is an option to play a few songs in kaffeine by typing the command : kaffeine 'song1' 'song2' 'song3'...

so i thought about a bash script which will concatenate all songs name from a file into one string named ,lets say, SONGS , and then execute the cmd :

kaffeine "$SONGS"
 
the songs file looks like this:
song1
song2
song3
...

so in c++ i'll do something like this:

[PHP]
Pseudo
-----------

string cSong // variable to hold the current song.
string SONGS // variable to hold all songs.

ifstream songsFile; // the file which contains all songs.

while(!songsFile.eof()) //continue while there is more data to read from file.
{
   getline(songsFile,cSong,'\n'); // write a single line to cSong.
   cSong+=" "; // add space after song name.
   SONGS+=cSong; // concatenate cSong to SONGS string.
}
[/PHP]

Can some one help me with an idea of making this algorithm in bash script?

THANKS.;)

---

### Post by Rany Albeg on 2008-08-30
Ok, thanks everyone , i'll go search in somewhere else.

---

