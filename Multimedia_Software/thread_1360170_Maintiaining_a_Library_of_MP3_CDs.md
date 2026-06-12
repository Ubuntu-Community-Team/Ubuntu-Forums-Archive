---
title: "Maintiaining a Library of MP3 CDs"
date: 2009-12-20
forum: Multimedia Software
---

### Post by krinchan on 2009-12-20
I work at a local bar and we maintain a book of MP3 CDs for nights when I'm bored, we don't have a professional DJ booked, and I want to look cool playing with the sliders and occasionally actually mixing some songs together. ;-)

On the windows side of things, I have a pretty convoluted tool chain for maintaining said book.  I usually maintain the playlists and burn the CDs in iTunes.  iTunes makes sure the MP3 files are renamed so that they are listed in the order they are on the playlist.  (This is important, as you'll see later.)  I then export the list and get a CSV file.  I have an Excel 2007 workbook with some macro's I made that dumps all the CSV files in the same directory into the spread sheets, deletes several useless columns, converts the time from total seconds into Excel's "fraction of a day" weirdness, and adds and fills a column with the numbered position in the playlist.  It was the lack of anyway to get iTunes to print a playlist with numbers along the left hand side that made me go to such lengths.

The numbers make my job easier because now I can grab a cd, slip it into our workstation, and punch in the number and get the track I want.

So, now that you have the context, I need to get some direction on gathering a suite of tools on Ubuntu to maintain this.  I could emulate the whole process from Windows, but it seems Rhythmbox doesn't burn CDs and I'm a bit clueless as where to go next.  Also, I don't think OpenOffice will like my Excel macros.  I've had massive issues with Excel macros in OO before.

However these are the things I absolutely need:

[LIST=1]
[*]to be able to burn a CD according to a playlist so that if I were to run ls on the CD, the file listing would be returned in the same order as the playlist
[*]To produce a track listing from the playlist or the set of MP3's on the CD. (Either is fine.  I can burn first then produce a listing or produce a listing then burn the cd.)  The track listing should be numbered, list pertinent information such as title, artist, album, length of track.  It can be a format like CSV that allows me to import into a spreadsheet for formatting and printing.
[/LIST]
If there's a program out there that does exactly this sort of thing, awesome.  If not, I'm not afraid of a bit of scripting and fidgeting to get things done.  I'm totally new to bash scripting though.  

Also, I've a vague feeling that there are command-line utilities that may let me extract information from the MP3 headers.  So I may be able to produce the CD, and run a script that'll simply loop through the files appending each file's info along with a counter variable into a CSV file for later use.  *shrug*

---

