---
title: "Cannot get Sopcast to work in Jaunty"
date: 2009-05-25
forum: Multimedia Software
---

### Post by groovybloke on 2009-05-25
Hi all !

I installed Sopcast in Intrepid and it worked fine. Since I installed Jaunty and then reinstalled Sopcast installation goes fine but when I try to invoke the program nothing happens !? Anybody had the same issue or have any suggestions ?

---

### Post by newseamus on 2009-06-02
same here. 

works on my Intrepid desktop, not on m jaunty laptop.

---

### Post by groovybloke on 2009-06-03
At least someone replied to my thread !! We should start a club - any help much appreciated even tho football season in the UK has finished.

---

### Post by newseamus on 2009-06-10
SOLVED!

In my case I had the sp-sc-auth file in the wrong folder. 
Someone on another board suggested i try cmd line to start*...then i saw that the system could not find that sp-sc-auth.

well I relocated the sp-sc-auth file to my home folder (my folder called "newseamus")

then i reinstalled the sopcast gui from here ([http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/))

now i have sopcast...

*
cmd line instructions:
copy and paste this into your terminal-
./sp-sc-auth sop://broker.sopcast.com:3912/6001 3908 8908 > /dev/null &

-if the terminal does nothing, you may be missing the sp-sc-auth file or it is not located where ubuntu can find it.

-if the terminal shows activity try the following:
open mplayer or vlc player and open this network---http://localhost:8908/tv.asf

hope this helps someone!

---

### Post by groovybloke on 2009-06-10
You - my friend are the MAN !!! Worked for me - thanks so much for your help.

---

