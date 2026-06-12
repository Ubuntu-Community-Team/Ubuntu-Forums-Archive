---
title: "What is the best music player software?"
date: 2008-04-30
forum: Multimedia Software
---

### Post by griehl2490 on 2008-04-30
I'm currently using rhythm box but I was wondering what the best music player/organizer is for Linux. I would like something along the lines of WMP or MediaMonkey for Windows. I just need smoething that can organize my music effectively (around 5500 songs). Also I was wondering if there was a program that does auto-organize like will organize all my music in a folder hierarchy.

---

### Post by Zorael on 2008-04-30
I like Amarok. As far as I'm aware it can't reorder your file hierarchy, but it has everything I'll ever need.

With how easy it is to install and uninstall packages, just pop up Add/Install and find Amarok. Or Synaptic and **amarok**.
```
$ sudo aptitude install amarok
```
Try it, then judge for yourself. The best way.

---

### Post by scragar on 2008-04-30
I like amarok(not rythm box, I could never figure it out in that.), if only for the podcasts thing, very nice being able to hear all my podcasts directly from the RSS.

---

### Post by griehl2490 on 2008-04-30
Amarok seems to be a little too bloated. Like I mean it has a lot of nice features but Just the view of it just seems like too much. Any other suggestions? Sorry, didn't mean to like shoot you down but I did install it and play around with it just to try out your suggestion :)

---

### Post by Whukes on 2008-04-30
I used RhythmBox for the longest time and then recently switched to QuodLibet and love it.  Ton of different options for viewing your music and very configurable.

```
$ sudo aptitude install quodlibet quodlibet-ext quodlibet-plugins
```

---

### Post by tubasoldier on 2008-04-30
XMMS is available. It is extremely similar to WinAmp Ver. 3.

I personally reccomend Amarok as well. It is by far the easiest to use and organizing your music can't be easier.

---

### Post by natrixgli on 2008-04-30
Wow this is such a matter of opinion, and I like several media players:

- Amarok is fantastic, I use it on my laptop when I DJ. 
- I use Rhythmbox at home because of DAAP. 
- I use Audacious with Streamtuner 'cause it's easier than th' Box.
- When I have guests, I use MP3blaster 'cause it keeps people from messing with the music. ;)


BTW You will find that XMMS is not in the repos any more, but Audacity is a near drop-in replacement. It's rad.

---

### Post by shinkaide on 2008-04-30
I'd have to say that AmaroK is the best, feature-wise. My iPod loves it, there's Last.fm integration, Musicbrainz, lyrics, and other cool stuff. I wouldn't say it's bloated... but that's prolly just me.

I also use Exaile, which is quite nearly an AmaroK clone, but is better suited to the Gnome environment. My only beef with Exaile is that it doesn't use Amarok's scoring system (0-100pts) and instead only uses the user rating system (1-5 stars), which is quite limiting, IMHO. If only Exaile could do that (can it? If it can, I don't know about it!) I'd drop AmaroK like a hot potato.

---

### Post by gigaSproule on 2008-05-02
I've been wondering the same thing. I hate Amarok. It is one of the worst programs I have ever seen. I really don't get why people like it so much. I find rhythm box nice to use (same nav as iTunes, which I love). This is probably one of the main reasons why my laptop isn't Ubuntu. I want a music player that organises my files in a hierarchy, like iTunes and is easy to use. But there is nothing out there.

---

### Post by MangasColoradas on 2008-05-02
> **Whukes said:**
> I used RhythmBox for the longest time and then recently switched to QuodLibet and love it.  Ton of different options for viewing your music and very configurable.

```
$ sudo aptitude install quodlibet quodlibet-ext quodlibet-plugins
```

Nice! Thanks. :)

---

### Post by ne4ve on 2008-10-08
> **gigaSproule said:**
> I've been wondering the same thing. I hate Amarok. It is one of the worst programs I have ever seen. I really don't get why people like it so much. I find rhythm box nice to use (same nav as iTunes, which I love). This is probably one of the main reasons why my laptop isn't Ubuntu. I want a music player that organises my files in a hierarchy, like iTunes and is easy to use. But there is nothing out there.

Because they've not used MediaMonkey!

I'm gonna post about a possible project I might start based on all the comments here and in many other posts on the forum. So keep your eyes open I'd like your collective thoughts.

---

### Post by fearful on 2008-10-08
I think this depends on your personal point of view. You can't decide based on other peoples opinion, fotunatley in Linux there is a wide variety of media players try different ones and see which one best fits your needs. Banshee, Songbird, AmaroK, Rythmbox, XMMS these are the ones out the top of my head, google is a good tool.

---

### Post by Day Tripper on 2008-10-08
Foobar2k through Wine :)

---

### Post by klikklak on 2008-10-09
I've mostly used quodlibet but in intrepid the packed 1.0 release doesn't start and 2.0 from source lacks plugins so I've switched to gmusicbrowser which, from a few days experience, seems to do a good job with my admittedly HUGE music collection.  All other players (rhythmbox, banshee, exaile) hang or crash with the collection, but this one works well.

---

### Post by uvdevnull on 2008-10-09
> **fearful said:**
> ... fotunatley in Linux there is a wide variety of media players try different ones and see which one best fits your needs. Banshee, Songbird, AmaroK, Rythmbox, XMMS these are the ones out the top of my head, google is a good tool.

And unfortunately, none of those have as good of a Media Library Manager as Winamp or iTunes.  Songbird comes close, but the Queue feature is deficient, as is Rhythmbox because they remove played songs so you can't go back and no double-click to queue functionality, you have to drag-n-drop.

All the other popular players like Amarok, Banshee, Exaile, Audacious have deficient MLs imho.  They're basically like file browsers, not real media libraries with filters.

People are always saying that XMMS and Audacious are "clones" of Winamp.  They are simply not.  Perhaps the basic player, but not the ML which is where Winamp's power lies.  Winamp has amazing library filtering and sorting, haven't been able to find anything like it for linux.  I'm in the process of going to linux full-time on my home lappy and this is an important aspect of that switch.

I think of all the players I've tried, and I've tried probably at least a dozen over the past month, Songbird comes closest, but still has some shortcomings.  I also feel that it has the most potential because it's extensible like Firefox with just plugins.

I've tried Winamp through Wine, but ML doesn't work.  At one point there was a Winamp port for linux but that didn't get traction either :(

I wish I was a little bit taller... I wish I was a coder... :)
(bonus points for guessing where this modified quote is from)

---

### Post by evilkastel on 2008-10-20
well, the quote sounds to me like seinfield, the chapter elaine draws a cartoon where a pig goes to a complain office and says "I wish i was a little taller" and is a clone of a ziggy, still as for music players, I also hate amarok. I use it everyday and I hate it. I am currently trying banshee and songbird, but if someone knows an equivalent of winamp or ever better, Aimp2, it'll be great.

---

### Post by uvdevnull on 2008-10-20
> **evilkastel said:**
> well, the quote sounds to me like seinfield, the chapter elaine draws a cartoon where a pig goes to a complain office and says "I wish i was a little taller" and is a clone of a ziggy,

That wasn't what I was thinking, but good call anyway, I totally remember that bit now! :)

What I was referring to was Skee-Lo's song "I Wish":
[http://www.youtube.com/watch?v=icr0eW1fRSs](http://www.youtube.com/watch?v=icr0eW1fRSs)

---

### Post by uvdevnull on 2008-10-20
> **ne4ve said:**
> Because they've not used MediaMonkey!

I'm gonna post about a possible project I might start based on all the comments here and in many other posts on the forum. So keep your eyes open I'd like your collective thoughts.

Did you get this going yet?

---

### Post by starscalling on 2009-01-21
> **uvdevnull said:**
> And unfortunately, none of those have as good of a Media Library Manager as Winamp or iTunes.  Songbird comes close, but the Queue feature is deficient, as is Rhythmbox because they remove played songs so you can't go back and no double-click to queue functionality, you have to drag-n-drop.

All the other popular players like Amarok, Banshee, Exaile, Audacious have deficient MLs imho.  They're basically like file browsers, not real media libraries with filters.

People are always saying that XMMS and Audacious are "clones" of Winamp.  They are simply not.  Perhaps the basic player, but not the ML which is where Winamp's power lies.  Winamp has amazing library filtering and sorting, haven't been able to find anything like it for linux.  I'm in the process of going to linux full-time on my home lappy and this is an important aspect of that switch.

I think of all the players I've tried, and I've tried probably at least a dozen over the past month, Songbird comes closest, but still has some shortcomings.  I also feel that it has the most potential because it's extensible like Firefox with just plugins.

I've tried Winamp through Wine, but ML doesn't work.  At one point there was a Winamp port for linux but that didn't get traction either :(

I wish I was a little taller... I wish I was a coder... :)
(bonus points for guessing where this modified quote is from)

```

Skee-Lo I Wish (Street Remix) lyrics
(Chorus)
(Skee-Lo)
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
(Skee-Lo)
I wish I was like six-foot-nine
So I can get with Leoshi
Cause she don't know me but yo she's really fine
You know I see her all the time
Everywhere I go, and even in my dreams
I can scheme a way to make her mine
Cause I know she's livin phat
Her boyfriend's tall and he plays ball
So how am I gonna compete with that
Cause when it comes to playing basketball
I'm always last to be picked
And in some cases never picked at all
So I just lean up on the wall
Or sit up in the bleachers with the rest of the girls
Who came to watch their men ball
Dag y'all! I never understood, black
Why the jocks get the fly girls
And me I get the hood rats
I tell 'em scat, skittle, scabobble
Got hit with a bottle
And I been in the hospital
For talkin' that mess
I confess it's a shame when you livin' in a city
That's the size of a box and nobody knows yo' name
Glad I came to my senses
Like quick-quick got sick-sick to my stomach
Overcommeth by the thoughts of me and her together
Right?
So when I asked her out she said I wasn't her type
(Chorus)
(Skee-Lo)
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
(Skee-Lo)
I wish I had a brand-new car
So far, I got this hatchback
And everywhere I go, yo I gets laughed at
And when I'm in my car I'm laid back
I got an 8-track and a spare tire in the backseat
But that's flat
And do you really wanna know what's really whack
See I can't even get a date
So, what do you think of that?
I heard that prom night is a bomb night
With the hood rats you can hold tight
But really tho' I 'm a figaro
When I'm in my car I can't even get a hello
Well so many people wanna cruise Crenshaw on Sunday
Well then I'ma have to get in my car and go
You know I take the 110 until the 105
Get off at Crenshaw tell my homies look alive
Cause it's hard to survive when your livin'
In a concrete jungle and
These girls just keep passin' me by
She looks fly, she looks fly
Makes me say my, my, my
(Chorus)
(Skee-Lo)
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
(Skee-Lo)
Hey, I wish I had my way
Cause everyday would be a Friday
You could even speed on the highway
I would play ghetto games
Name my kids ghetto names Little Mookie, big Al, Lorraine
Yo you know that's on the real
So if you're down on your luck
Then you should know just how I feel
Cause if you don't want me around
See I go simple, I go easy, I go greyhound
Hey, you , what's that sound?
Everybody look what's going down
Ahhhh, yes, ain't that fresh?
Everybody wants to get down like dat
(Chorus)
(Skee-Lo)
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
I wish I was little bit taller
I wish I was a baller
I wish I had a girl who looked good I would call her
I wish I had a rabbit in a hat with a bat
And a six four Impala
Yeah
You know, you know, you know Skee-Lo
Wish you were taller wish you were a baller
Skee-Lo you know, you know, you know
Wish you were taller wish you were a baller
You know, you know, you know Skee-Lo
Wish you were taller wish you were a baller
Skee-Lo you know, you know, you know
Wish you were taller wish you were a baller
You know, you know, you know Skee-Lo
Wish you were taller wish you were a baller
Skee-Lo you know, you know, you know
Wish you were taller wish you were a baller
You know, you know, you know Skee-Lo
Wish you were taller wish you were a baller
Skee-Lo you know, you know, you know
Wish you were taller wish you were a baller

```


anyhow... so i personally like quodlibet however i actually found this thread looking for something to auto-arrange the files themselves.....

will check back in if i find something good.... personally i like to go in artist > album format - let genre take care of its self.. might have to just make a little scripty ;)

---

### Post by HunterK on 2009-01-21
I find exaile does everything I need.  It also is a gnome app.  If I am correct, when you install amarok in gnome, you need to also install all of the libs required to run a KDE app in gnome.

I like exailes ability to go to the wiki page of a bank, grab lyrics, fetch album art, easily modify large groups of ID3 tags.

---

### Post by krul on 2009-01-21
> **HunterK said:**
> I find exaile does everything I need.  It also is a gnome app.  If I am correct, when you install amarok in gnome, you need to also install all of the libs required to run a KDE app in gnome.

I like exailes ability to go to the wiki page of a bank, grab lyrics, fetch album art, easily modify large groups of ID3 tags.


I agree, I love Exaile....simple but powerful. Especially the dynamic mode

---

### Post by uvdevnull on 2009-01-21
> **starscalling said:**
> 
Skee-Lo I Wish (Street Remix) lyrics
(Chorus)
(Skee-Lo)
I wish I was little bit taller
I wish I was a baller
...


+10 points to starscalling :)

---

### Post by tv0571 on 2009-01-21
For those contemplating an upgrade to Quod Libet 2.0, you may want to stay with your current version unless you are good at compiling.  I could only find a package for Ibex -> after upgrade to Ibex, Synaptic said I needed to purge a Nvidia package (nvidia-glx)-> after purging that package and after rebooting -> no sound card, and nothing I've tried so far will get it back.  Now no sound.

---

### Post by juny20 on 2009-01-30
I was searching and trying all music players out there. I used Amarok for a few months, but yesterday installed Songbird. So far, I love it. Extensible via add-ons like Firefox. Super easy. It scanned my music collection in no time (about 7,000 songs). It has eye candy if you like that. Start up time is very fast. I am still getting use to it and learning about it, but it exceeded my expectations. So far, I find it far superior than Amaron, Banshee, Rythbox, etc...on features and performance.

---

### Post by centos on 2009-01-30
Songbird has fine features but is way too slow. I'm currently using Banshee, but I totally miss foobar2k.

I'm looking for something that handles well compilations. Almost every player I tried shows only artist, so after adding compilation album (like soundtrack) to the library it creates many artist which has only one track. Is there any player that would read the Album artist tag (eg. Various artists) and then showed it as a Various amongst other artists with regular albums?

---

### Post by DeMus on 2009-01-30
I just stick with Rythmbox. I have used some others but they were not what I was looking for. Amarok is something I will never use again, so is Realplayer (with their aggressive install methods), Banshee and Exaile are just so-so.
I can do what I want with Rythmbox so that is what I use. I play my MP3s, I play my FLACs, my OGGs and I listen to radiostations worldwide.
I don't need playlists although Rythmbox also can do that. I just one long list (9031 songs and albums) and I choose what I like to hear. I start it, minimize the program and do what I want to do.

Go Rythmbox, Go.

---

### Post by noteviljoe on 2009-05-06
All I want is to be able to browse through my albums displayed as album art. I don't know how anyone finds scrolling through text satisfying :-(

On Windows I used Media monkey, which had great album scrolling. I was also flirting with songbird, which has really brilliant web integration though it lacks full m4a support. I'm going to give installing sonbird a try though being new to Ubuntu I am a bit nevous about the fact that I can't install it through the add/remove tool but have found it at [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by salvachn on 2009-05-06
Audacious and Songbird. Like Winamp and iTunes!

---

### Post by me.translucent on 2009-05-06
songbird !!!... i hate the fact that it's damn too slow and becomes unresponsive too many times ..i try to use it ignoring the fact and always keep a killall songbird-bin handy :P .but future for songbird seems bright!!..

---

### Post by Snyper450 on 2009-05-06
Stay with Rhythmbox it runs fine doe everything xD

---

### Post by Snyper450 on 2009-05-06
NOO!!! Stay with Rhythmbox why fix a not broken thing xD:P

---

### Post by slakkie on 2009-05-06
It is not really what you are looking for but I use mplayer and some shell functions to create playlists from my music folder:

```

make_playlist () {
        find -L $HOME/slakkie/home/music -iname \*.mp3 -o -iname \*.ogg -o -iname \*.flac | sort > $HOME/media/playlist
}

play_music () {
        local OPTIONS
        [ -n "$1" ] && OPTIONS="-shuffle "
        eval mplayer $OPTIONS -loop 0 -playlist $HOME/media/playlist
}

play_artists () {
        local playlist=$HOME/media/playlist.artist
        : > $playlist
        for i in "$@"
        do
                if [ -n $artists ]
                then
                        grep -i $i $HOME/media/playlist >> $playlist
                fi
        done
        if [ $(stat -c %s "$playlist") -ne "0" ]
        then
                eval mplayer $OPTIONS -loop 0 -playlist $playlist
        fi
}

```

It doesn't organise the music, but since I rip my own CD's with abcde I don't feel the need to organize my music even more.

For me this is the best music player a man can have, I usually use screen where I start mplayer, then detach it, and just listen to the tunes. If I logout from my PC the music keeps playing, so any unfortunate crash of X, or other accident, I can at least listen to music while fixing the issue :popcorn:

---

### Post by tv0571 on 2009-05-06
NotevilJoe, Quod Libet has a plugin that downloads cover.jpg 's so that you can see the cover art for your album in the album list.  Works pretty well.

---

### Post by noteviljoe on 2009-05-09
> **tv0571 said:**
> NotevilJoe, Quod Libet has a plugin that downloads cover.jpg 's so that you can see the cover art for your album in the album list.  Works pretty well.

I've got most of the album art I need -- what I want is to be able to browse my albums via it. I honesty can't understand why this isn't more of a priority for people ???

Just given Quod Libet a try, its nice but it isn't quite the view I'm looking for. The text takes up more room then the little pic's of the album covers. I crave the reverse.

In media monkey you can see all the alumbs up in a grid and its loverly. (see [[IMG]http://img13.imageshack.us/img13/3587/mediamonkeyrocks.th.jpg[/IMG]](http://img13.imageshack.us/my.php?image=mediamonkeyrocks.jpg))
In Song bird you can get a loverly line of large album covers that flow.

---

### Post by ptipton on 2009-05-12
> **centos said:**
> Songbird has fine features but is way too slow. I'm currently using Banshee, but I totally miss foobar2k.

I'm looking for something that handles well compilations. Almost every player I tried shows only artist, so after adding compilation album (like soundtrack) to the library it creates many artist which has only one track. Is there any player that would read the Album artist tag (eg. Various artists) and then showed it as a Various amongst other artists with regular albums?

Did you come up with anything that works ok with various artists? I play my music through XBMC so am looking for a program to rip disks to flac, tag properly including the albumartist field and cover art and is good at making playslist. Wouldnt have thought this was too much to ask but just tried Amarok, Exhaile, Banshee and rythmbox and non of them can do this easily and they seem to handle various artists as different albums as you mention. Best i can get so far is to rip with soundjuicer and tag with either Kid3 or remotely from a windows machine with Foobar- oh for Fobar for linux!

---

### Post by brett- on 2009-05-25
I used Amarok up until the 2- "upgrade", the equalizer was removed and that is a bad thing:     Switched to Exaile, excellent interface (like Amarok), has equalizer with pre and user def presets and best tag editor I have seen.    Album art fetcher falls short though:  Integrated "streamripper" works fine, can review stations with id tags:    I use it to control 480 watt Marshall Leach amp (see [http://ubuntuforums.org/showthread.php?t=686279&highlight=leach&page=174](http://ubuntuforums.org/showthread.php?t=686279&highlight=leach&page=174))

---

