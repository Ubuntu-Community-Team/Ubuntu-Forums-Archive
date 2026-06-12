---
title: "MythMusic - Repeat All"
date: 2010-04-27
forum: Mythbuntu
---

### Post by techstop on 2010-04-27
Hi all. I've had this annoying problem for a while now. If I go to mythmusic to play some music, the "Repeat" setting will be mysteriously set to "All" (ie this is where you press "2" to change between None, All etc). I'll set it to None, then listen to my music.

Somehow it gets changed back to "All" again, and the first I'll notice is days later when I put some music on again, Repeat is set to All again and I'm listening to the first track of an album again.

I thought it might have been a bug with 9.10, but I've since done a fresh install with 10.04. Then I thought it might be the Logitech Harmony universal remote, so I stopped using that and went back to separate MCE remote, amp and TV remotes etc.

This really has me baffled and I'd be really grateful if someone can help me out here.


FWIW, I'm using 10.04 x64.

Cheers...

---

### Post by matt06 on 2010-04-27
This behavior sounds familiar.  I don't use MythMusic much, but I do recall seeing the Repeat setting changed when I did not alter it. This is on 9.10 with 0.22+fixes (23893).

---

### Post by techstop on 2010-04-29
Bump! Any fixes for this annoying problem?

---

### Post by Point &amp; Click on 2010-11-04
Hi,

  I realise this is an old(ish) thread, but this was bugging me too, so I decided to have a look in to it.

  It turns out that (for whatever reason), Myth isn't writing that value back to the database when you change it. And if there's no setting in the database, guess what the default is...?

  "All".

  So, I looked into writing up this bug, but it appears that MythMusic is planned to be re-written anyway:
[http://svn.mythtv.org/trac/wiki/FutureDevelopment](http://svn.mythtv.org/trac/wiki/FutureDevelopment)

  So I don't think there's much point in reporting it at the moment... 

  Anyway, I thought I would reply with my workaround so that fellow searchers would find this and be able to make their desired default stick.

 Note: This will just allow you to change the default, it won't fix the bug whereby the option is saved each time.

So, depending on your installation (*buntu+Myth, or Mythbuntu, etc), you might need to install myphpadmin (it's in the repositories if it's not installed already).


[LIST]
[*] Open a web browser and go to [localhost/myphpadmin]("http://ubuntu-ky.ubuntuforums.org/localhost/myphpadmin")
[/LIST]
You will need to know your Myth password - it's the first page under Setup-->General on the FrontEnd settings.
[LIST]
[*] Login as mythtv / <your password>
[*] On the left-hand column, click on "mythconverg" to select that database
[*] Now a list of tables appears, scroll down to "settings" and click on it.
[*] On the main phpMyAdmin window, click on the "Insert" tab near the top of the webpage.
[*] A form appears
[/LIST]
 You need to fill in the "value" column on the right-hand side as follows:

[LIST=1]
[*]1st row should read:  ```
value varchar(129) RepeatMode
```
[*]2nd row should read: ```
data text none
```
[*]3rd row should read: ```
hostname varchar(64) <the name of the computer>
```
[/LIST]

So, in my example, the right-hand column on my media pc reads:
```
RepeatMode
none
TranquilityBase
```[B]

Note[/B]
If you want the default repeat mode to be track, then make that 2nd row read "track" ;)


[LIST]
[*] Now click on the "Go" button
[*] Then click on the "Search" tab (we should check it put the value in correctly)
[*] Just put RepeatMode in the first seach box (for the "value" field) and click the "Go" button
[/LIST]
 
If all went well, you should see 1 line (just below the middle of the page) with the values you entered earlier.

It worked for me, I'm sure it will for you :)

And relax...

---

### Post by alien878 on 2010-11-04
Thank you Point & Click!  I figured it was a stuck setting in the DB, but I couldn't figure out which one.

BTW:  If you don't want to install myphpadmin, it can be done from the command line (replace YourPassword and YourHostName as appropriate):

```
mysql -umythtv -pYourPassword mythconverg
mysql> insert into settings ("value","data","hostname") values ("RepeatMode","none","YourHostName");
mysql> exit;

```

---

### Post by techstop on 2010-11-05
> **Point & Click said:**
> Hi,

  I realise this is an old(ish) thread, but this was bugging me too, so I decided to have a look in to it...

Thanks so much. My myth box is semi-retired at the moment (trialling a FetchTV box), but will make those db changes when I turn it back on.

Cheers!

---

