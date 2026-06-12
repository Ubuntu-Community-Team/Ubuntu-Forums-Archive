---
title: "MediaMonkey Ratings to Banshee Guide"
date: 2011-04-17
forum: Multimedia Software
---

### Post by Akovia on 2011-04-17
I have searched for a solution to this and have only found remarks stating that ratings are incompatible between most media players due to no comprehensive standard yet. With that said, I found no real solutions or work-around other than to deal with it.

Well this may be obvious to some, but here was how I dealt with it.

**1.** Sort your entire library in MM by ratings.
**2.** Select all the 5 star songs and send to a new playlist
**3**. R-Click the playlist and Send To -> Export to M3U Playlist
**4.** Rinse-Repeat for the other star ratings
**5.** Open up each M3U playlist in your favorite text editor within Linux to save with proper formatting (I used gedit)
**6.** Replace all **[COLOR="DarkRed"]\[/COLOR]** with **[COLOR="#8b0000"]/[/COLOR]** and save. 
**7.** Import each playlist into Banshee
**8.** Select all songs in each imported playlist and R-Click to set proper rating. 


***Notes & Disclaimers:***

**-** I have my music on an external drive, so both programs were using the same root directory. If you are moving your music instead, you will have to reflect that new path as well during the search and replace.

**-** When replacing the slashes to reflect unix paths, there is the possibility of changing a slash in a song title and there is most definitely better ways to do this via sed scripts or playlist conversion utilities. Writing a script or searching for even more software was more than I wanted to do and it all worked fine for me. Your mileage may vary.

**-** Banshee does not support the 1/2 star ratings of MediaMonkey so you will have to decide how you want to handle that. The two obvious options are to..

-- **1.** Round the star ratings when creating the playlists in MM which will cut your time down by half.

-- **2.** Create a playlist for all star ratings and have those playlists available in Banshee to use and add to, and hopefully in the future when/if Banshee supports finer grain control, you won't have to re-rate the songs. This is what I did and rounded them in Banshee, but still know what my half star rating is from the playlists.

**-** I would recommend to set up Banshee to write the ratings to the tag before setting the new ratings. At least the ratings (albeit coarse) will be attached to the actual songs for any other future uses. I figure open source will be the first people to adopt a standard if one is ever decided upon.



All in all, it took me about 15 minutes to do this for my 7K+ song library that had 2K+ already rated. A good part of that was waiting for my old laptop and MM running under Wine on it. I'm sure it could be done much faster on a better machine. Not a bad time investment if you ask me, but I didn't have much of a choice as I'd still prefer to use MM if I could but it's just too sloooooow, and the features I love are neutered under Wine anyway.

If someone has an easier way to do this or wants to add to it, please feel free. This place has helped me so much and am just trying to give back. 

Ako

---

