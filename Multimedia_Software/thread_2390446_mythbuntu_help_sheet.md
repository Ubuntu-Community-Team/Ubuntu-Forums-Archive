---
title: "mythbuntu help sheet"
date: 2018-04-28
forum: Multimedia Software
---

### Post by benlyboy on 2018-04-28
I was going through HD of mine and came across this file i had written to help a friend out. thought it might be useful to someone so i thought i would post it. This isn’t all new stuff, a lot of it i got off this very forum, but its now all in one place.  maybe others have other tricks they have found over the years and can post them?

Hope this helps someone :)

                                      Things I do to, or know about mythbuntu

First if you’re going to use a remote with your system, set it up during the install. Doing this in my experience always seem to work, I’ve run into problems a few times trying to set it up later. Not all the time but why take the chance.

If you are setting up a remote frontend you need to know the mythbackend user name and password these can be got from this file “home/.mythtv/config.xml” on your backend. And then just put the info in the same file on your frontend.

Sometimes the front end will start before the computer has established a wifi connection or the backend has booted in the case of a all in one system. To delay the front end add “sleep 3” ( 3 = 3 seconds, you can use what ever number you need) to the very beginning of this file “ /usr/bin/mythfrontend”, my understanding is that this works with the back end too using “/usr/bin/mythbackend” in the same way.

If you need to minimize mythfrontend to work on your desktop use ctrl+alt+d. 

I had a problem with the front end not opening up. It would look like my computer had frozen up, no mouse nothing. What had actually happened was myth had opened with a pic of my desktop hitting ctrl+alt+d minimized the front end and mouse was back. To fix this you must remove mythmusic
“sudo apt-get purge mythmusic” don’t know why this works, I found this info on line, and it has worked for me a couple of times.
 
Mythweb failed to show listing or recordings instead showing an error something like this
 !!NoTrans: SQL Error: Expression #3.
For me the fix was to add this line(“ sql_mode=NO_ENGINE_SUBSTITUTION “)  to the bottom of this file (“ /etc/mysql/conf.d/mythtv.cnf”)


To fix no video play back on mythweb
There are two main problems that I found, they are in the following file.

/usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php 

First is that the program or script (to be honest not sure which is the right term) is looking for a file called ffmpeg that I believe is actually called mythffmpeg. This was an easy fix, i simply went in and made a copy of the file and named this copy ffmpeg. I kept the original as it maybe need somewhere else.

The second thing is that the Split() command  was removed from php 7.0.0 . I know nothing about PHP so I went looking on line for info, I found that split() had been replaced with explode(), but I couldn’t find much on if they were formatted the same, in the end I just replaced Split with explode and it just worked, so I guess they are formatted the same

---

