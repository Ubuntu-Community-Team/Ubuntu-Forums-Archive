---
title: "Combining Existing Backends"
date: 2011-04-23
forum: Mythbuntu
---

### Post by crbnrod on 2011-04-23
I should mention up front that this is either:
1. a dumb/obvious question
2. evidence I'm bad at using the search tool
3. proof I'm a trailblazer (*highly* unlikely given my lack of expertise...)

Now then - I have two existing FE/BE machines that receive different TV feeds. I want to set them up to share content, but I don't want to lose any recordings that already exist on either of them. i.e. when I changed one from a primary BE to slave in the mythbuntu control center, the database for that particular BE went away and I had to restore it.

Is what I want to do as simple as correctly setting the IP addresses &c in the general backend setup & the frontend database config, or is there something else that will need to be done? I realize I could just try updating the settings, but since I've already killed & revived one database, I thought I'd make sure before proceeding again.

---

### Post by crbnrod on 2011-04-23
After some poking around, it appears I am going to run into a database problem if I just change IP addresses in the setup. I can get the machines to see recordings on the other machines, but in doing so they're not able to see recordings on themselves (e.g. on the backends attached to each frontend).

Anyone have any ideas? I suppose I could export the recordings from one machine to another and then set up as a slave BE, but then I'd be losing the database from the slave BE and would get all kinds of double recordings & so on.

---

### Post by bance on 2011-04-25
See [_[COLOR=Red]this[/COLOR]_]("http://www.gossamer-threads.com/lists/mythtv/users/478433") post...... also there was a post a few weeks back in this forum where somebody did a similar thing, to what you're trying to do. Maybe search for moving recordings?

HTH Steve

---

### Post by crbnrod on 2011-04-25
Thanks for the response. I have found some stuff about moving recordings - I think one option I have would be to move the recordings on one backend to mythvideo on the other backend, then change the (now empty) backend into a slave. The problem there is then I lose the database of previous recordings & all recording rules on the emptied-out backend and so on. Which in the long run I guess would work ok, but is a fair amount of tedious work up front, as well as the annoyance of deleting rerun recordings on an ongoing basis (first world problems, I know).
I wasn't able to get your link to work. I've seen a couple threads here and there, but not much where anyone's actually combining existing databases.



I did find this on the mailing list, but it's pretty far over my head and I'm not sure if it's exactly what I'm trying to do, either. My SQL knowledge is so basic as to be nonexistent.

[http://www.gossamer-threads.com/lists/mythtv/users/381417?search_string=merge;#381417](http://www.gossamer-threads.com/lists/mythtv/users/381417?search_string=merge;#381417)

Maybe someone who's more SQL-saavy than me can tell me if that's what I'm looking to do and how tricky it actually would be.

---

### Post by bance on 2011-04-25
Try the link again..... Also [_[COLOR=Red]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1709134") one

HTH Steve

---

### Post by crbnrod on 2011-05-17
Thanks for the help. Given my lack of expertise and how much my wife hates missing Bones, I decided the safest thing was the mythvideo backup route.

Once I figured out how myth determines the filename in the recordings directory, it wasn't all that much work to figure out what was what and copy it to the videos directory, especially given I was looking at the possibility of hosing two databases.

---

