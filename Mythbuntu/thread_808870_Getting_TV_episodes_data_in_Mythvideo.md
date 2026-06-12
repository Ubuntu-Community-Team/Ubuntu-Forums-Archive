---
title: "Getting TV episodes data in Mythvideo"
date: 2008-05-26
forum: Mythbuntu
---

### Post by uMuppet on 2008-05-26
I have a lot of TV episodes in my Mythvideo collection but the default imdb search doesn't work for TV episodes.  IMDB.com does not have a very good archive of TV episode data either, a far better one is tvrage.com

Has anyone got a skimmer to get data for TV shows?  
Has anyone got internal imdb skimmer to successfully get data for TV episodes?

---

### Post by toorima on 2008-05-26
there is a script called metacleanup that gets info for tv shows, you can find it at [http://idisk.mac.com/r.mcnamara-Public?view=web](http://idisk.mac.com/r.mcnamara-Public?view=web) it will also take a screenshot from the file and use as icon.

---

### Post by uMuppet on 2008-05-27
Nice one, thanks.  Have you had this script working?

---

### Post by toorima on 2008-05-27
Yeah I use it all the time, I have another script for imdb so I run that first then metacleanup to take all files that imdb can't do.

---

### Post by uMuppet on 2008-05-27
Works great, thanks alot.  this one has been bugging me for a while.

---

### Post by toorima on 2008-05-27
Glad you liked it

here is some more info about the script
[http://www.mythtvtalk.com/forum/viewtopic.php?t=7077&highlight=imdb+bulk](http://www.mythtvtalk.com/forum/viewtopic.php?t=7077&highlight=imdb+bulk)

and there is a nice bulk update script for imdb
[http://www.mythtv.org/pipermail/mythtv-users/2007-September/195918.html](http://www.mythtv.org/pipermail/mythtv-users/2007-September/195918.html)

---

### Post by usererror on 2008-05-27
Does the above script for tv shows tie into the imdb.pl ??

Or do you run this tv episode script manually from a terminal?

---

### Post by toorima on 2008-05-27
I run it manually from terminal but I guess one could write a short script that would run the imdb bulk update script first and then run metacleanup. You always want to run the imdb script first otherwise the metacleanup script will process the movie and it won't get the right info.

---

### Post by malaTG on 2008-07-02
Hi everyone,

I have ripped my Friends episodes to my harddrive and now I want to use the metacleanup script to fix all information. I have tested it and it works correctly, however I don't want to answer y and the enter on each episode. I am no perl programmer but couldn't I change 

>                        print "Do you want to add this to the Myth Database? (y/n)\n";
                       chomp(my $answer = <STDIN>);
       #               $answer = <STDIN>;
                       if ($answer eq "y") {
                               addrecord(@showinfo, $inputfile,$fullpath);
                               #exit (-1);
                               $laststate = -1;

in the tv rage perl scrip to something like

>                        #print "Do you want to add this to the Myth Database? (y/n)\n";
                       #chomp(my $answer = <STDIN>);
                       $answer = y;
                       if ($answer eq "y") {
                               addrecord(@showinfo, $inputfile,$fullpath);
                               #exit (-1);
                               $laststate = -1;

and it would work?

/Marcus

---

### Post by toorima on 2008-07-02
In tvscript.sh you want to change this line
```

perl $RAGESCRIPT --dbhost=$SQLSERVER --dbname=$DBNAME --dbuser=$DBUSER --dbpass=$DBPASSWORD --prefix=$MOVIEHOME "$videofile"
```
just add -i after $RAGESCRIPT so it looks like this
```

perl $RAGESCRIPT -i --dbhost=$SQLSERVER --dbname=$DBNAME --dbuser=$DBUSER --dbpass=$DBPASSWORD --prefix=$MOVIEHOME "$videofile 
```
you might get some funky result sometimes from tvrage but just move the files out from your video directory and update video database and move them back in again or you can edit stuff in phpmyadmin to fix details

---

### Post by malaTG on 2008-07-02
Thank you! :-)

---

