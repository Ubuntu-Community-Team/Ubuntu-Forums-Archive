---
title: "Tangerine Shares No Music When Finding Music in Banshee"
date: 2009-05-18
forum: Multimedia Software
---

### Post by GenuineXP on 2009-05-18
I just installed Tangerine to share music from my desktop via DAAP. It seems quite nifty, but it doesn't want to share music from my Banshee database.

When I tell Tangerine to share all the music from a directory, it seems to work, but I lose a lot of information that I organize with Banshee (such as compilation artists, etc.). Since I organize my music with Banshee, I set Tangerine to share music it finds in Banshee. I assume this means it reads Banshee's database and shares music using that information.

Well, when I try this Tangerine shares nothing. No songs. Nadda. Could there be a version incompatibility or something? I'd like for this to work, since sharing from the directory has some messy results for DAAP clients, such as multiple entries for the same album!

Any ideas? Thanks!

---

### Post by GenuineXP on 2009-05-19
Bump.

---

### Post by GenuineXP on 2009-05-24
Bump.

---

### Post by GenuineXP on 2009-05-28
Bump.

Out of curiosity, has anyone else even encountered this problem?

---

### Post by Noah0504 on 2009-05-30
I've come across the same problem.  I just had to point Tangerine to the music folder I used with Banshee and everything worked fine.  Tangerine is easy, but I'm looking to see if there isn't a more elegant solution.

---

### Post by Winterstorm on 2009-07-13
Today I tried this whole Banshee / Tangerine thing:

Two things have changed: 


[LIST]
[*] the banshee.db path is hardcoded and changed from  .gnome2/banshee/banshee.db to .config/banshee-1/banshee.db (For most other people I guess it should be .config/banshee-1/banshee.db)
[LIST]
[*](I think this parameter should be relocated into some config file...)
[/LIST]
 
[*]The Banshee Database format has changed. (The SQL query is now a little more complex.)
[/LIST]

I fixed an "exception" issue, causing random crashes when tangerine updates its internal  "tracklist".

I attached a Patch for the SVN version.

(Remember to modify the banshee.db path)

Get the sources (as described on  [http://www.snorp.net/pages/tangerine](http://www.snorp.net/pages/tangerine))

Then apply the patch in: tangerine/plugins/banshee/
$ patch BansheePlugin.cs BansheePlugin.cs.svn.patch.txt


HTH. 

(I'm not even sure I will use banshee any longer since I encountered several crashes... over the last hour.)

---

### Post by mole84 on 2009-07-23
> **Winterstorm said:**
> Today I tried this whole Banshee / Tangerine thing:

Two things have changed: 


[LIST]
[*] the banshee.db path is hardcoded and changed from  .gnome2/banshee/banshee.db to .config/banshee-1/banshee.db (For most other people I guess it should be .config/banshee-1/banshee.db)
[LIST]
[*](I think this parameter should be relocated into some config file...)
[/LIST]
 
[*]The Banshee Database format has changed. (The SQL query is now a little more complex.)
[/LIST]

I fixed an "exception" issue, causing random crashes when tangerine updates its internal  "tracklist".

I attached a Patch for the SVN version.

(Remember to modify the banshee.db path)

Get the sources (as described on  [http://www.snorp.net/pages/tangerine](http://www.snorp.net/pages/tangerine))

Then apply the patch in: tangerine/plugins/banshee/
$ patch BansheePlugin.cs BansheePlugin.cs.svn.patch.txt


HTH. 

(I'm not even sure I will use banshee any longer since I encountered several crashes... over the last hour.)

Completing the Fix:

Its kinda tricky to get the tangerine code to compile from the svn trunk, I found these tricks useful

[LIST=1]
[*]Get Dependencies: To compile you need daap-sharp installed which can be found at [http://www.snorp.net/pages/daap-sharp](http://www.snorp.net/pages/daap-sharp), download the source package and extract. 

To compile daap-sharp and tangerine you need gmcs so: ```
sudo apt-get install mono-gmcs
```, coincidentally the gmcs is a new version and the binary is now named gmcs2 so the configure files error out, my fix to this was to create a hard link from a dummy gmcs library to gmcs2: ```
sudo ln /usr/bin/gmcs2 /usr/bin/gmcs
```, now you should be able to compile daap-sharp using ./configure then make then sudo make install.

Next download the svn source of tangerine and apply the patch as described by Winterstorm.

To compile tangerine you need another package named libtool so ```
sudo apt-get install libtool
```
[*]Compile:
Now you should be able to compile tangerine first by running ./autogen.sh. That should create the make file for you so then run make, and finally sudo make install. 
[*]Install:
The install isn't formulated for debian so in order to make the binaries available in the default path ```
sudo cp /usr/local/bin/tangerine /usr/local/bin/tangerine-properties /usr/bin/
```
[/LIST]

The patch that was posted previously is a step in the right direction especially with updating the path of the banshee db, however, i notice another problem that it cant read in files that are not on the main system hard drive. However, it is working for files stored on the main hardrive, im guessing a query or regex needs to be updated.

---

### Post by directhex on 2009-07-23
If this patch can be cleaned up to not cause the issue mole84 cites, then it should be submitted as a bug against the Debian package - and we can include the patch in the packages.

---

### Post by mole84 on 2009-07-24
ahh the joys of hacking...

So as it turns out the previously discussed error of the files not being found was happening because of another banshee database update. Basically they added a field "UriType" to the CoreTracks table of the database. This field delimits whether or not the said file is in the Banshee "Music" folder which is one of the user settings in Banshee. If the file is in the Music folder then the URI in the database for the file does not contain the complete uri, strangely enough if the file is not in the Music folder then the database contains the complete URI for the file. 

As it turns out the variable for where the user set the Music folder to be is in a slimy XML file located at ~/.gconf/apps/banshee-1/library/%gconf.xml

So this patch attempts to parse out that location and add it to the file URIs as necessary. The code is not necessarily hardened but hey, it worked on my box, please let me know if anyone is able to replicate the success. 

This patch contains all the previous updates listed by Winterstorm as well so you only need to patch the svn version once. Follow the previous two posts to apply the patch and then build a new copy of tangerine!

---

### Post by directhex on 2009-07-24
I'll try to take a look this evening.

---

