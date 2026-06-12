---
title: "get_iplayer change output folder"
date: 2012-05-27
forum: Multimedia Software
---

### Post by bill-lancaster on 2012-05-27
How can I change the default directory for recordings?
This command "get_iplayer --output="/home/bill/Music/recordings" just results a listing of all programmes.

Any ideas?

Ubuntu 12.04
KDE 4.8.1

---

### Post by shantiq on 2012-05-27
hi Bill [**from man page**]("http://manpages.ubuntu.com/manpages/lucid/man1/get_iplayer.1.html")

> --output, -o <dir>
              Recording output directory



add at the end  or anywhere else      example


> get-iplayer   --vmode=flashvhigh2 --get 4    --subtitles-only [COLOR="DarkRed"]--output ~/Music/recordings[/COLOR]



> get-iplayer   [COLOR="DarkRed"]-o  ~/Music/recordings [/COLOR] --vmode=flashvhigh2 --get 4   --subtitles-only 



other  refinements

> --outputliveradio <dir>
              Output directory for live radio recordings

       --outputlivetv <dir>
              Output directory for live tv recordings

       --outputlocalfiles <dir>
              Output directory for localfiles recordings

       --outputpodcast <dir>
              Output directory for podcast recordings

       --outputradio <dir>
              Output directory for radio recordings

       --outputtv <dir>
              Output directory for tv recordings

---

### Post by bill-lancaster on 2012-05-27
Thanks for the response.

What I should have said is "how do I change the setting for the default folder"

In my previous installation I managed to do it but have forgotten how!

I suppose the question could also be "how can I edit the output settings"

Thanks again

---

### Post by bill-lancaster on 2012-06-24
Found it!
This is the code I used:-
"get_iplayer --prefs-add --output "/home/bill/Music/recordings"

---

### Post by Cheesemill on 2012-06-24
I have a couple of aliases set up in my ~/.bashrc file:
```
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output /data/Videos/ --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
```
This way I can just do:
```
ipl <string>
```
to search for a program and then
```
gipl <pid>
```
to download a program at it's highest quality into my Videos folder.

---

### Post by shantiq on 2012-06-24
thanx for tips guys


this will simplify my situation

```
get_iplayer --prefs-add --output "Videos"
```

---

### Post by shantiq on 2012-06-25
also this to make radio program download so much easier


1.   in terminal   enter   >  alias getradio='get-iplayer -o ~/Music   --mode=flashaacstd --get'

then again open ```
gedit ~/.bashrc
``` and enter at bottom
```
alias getradio='get-iplayer -o ~/Music   --mode=flashaacstd --get' 

``` and save

2.   ```
. ~/.bashrc
```

3.   now    all you need    is    this


```
getradio   13434
```      or whatever number you seek to download

goes to your music folder

---

### Post by bill-lancaster on 2012-06-26
Wow!  That's rewarding.
Lots of neat things to try!

Thank you all.

---

### Post by Merrattic on 2013-02-10
Setting output folder manually:

Browse to ~/.get-iplayer

If you have a file called options, good, if not create it:

```
touch ~/.get-player/options
```Open this file in your preferred text editor

Add your preferred download directory like this:

```
output Videos
```and save.

There is also a global options file in /etc/get-iplayer you can edit, but you will need root for that, and if you have multiple users, use a non home directory folder with full path and permissions.

---

### Post by kernowkoi on 2013-04-19
Hi All,

I have be using the --output(-o) option. but have run into some strange behavior   If I run a get_iplayer cmd manually on the command line all good but if I try the same command line in a Bash script the output ends up in a different directory to what I specified with the --options switch

Example Cmd line works just fine

get_iplayer --force --overwrite --nopurge --type=radio --pid=b01rz317 --output "/home/htpc/Videos/iPlayer/Radio/BBC Radio 4" --file-prefix="<name>-<episode>-<pid>"

same thing in a script and somewhere while running get_iplayer converts the output directory to

'/home/htpc"/home/htpc/Videos/iPlayer/Radio/BBC"

Which results in a nonsense directory structure in my home user folder
Notice how it added my user home directory to the front and chopped off the last bit of the path I supplied via --output option!

Reading the posts on this thread I conclude that get_iplayer is picking up some 'default' output folder and prefixing whatever I specify with the --output option

Where from??  and Why only when running inside a  BASH script

Annoying as it was all going so well, automating downloads of recordings into mythtv

Any suggestions please

---

