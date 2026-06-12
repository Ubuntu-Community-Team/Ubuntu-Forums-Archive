---
title: "Pithos stopped working?"
date: 2014-12-12
forum: Multimedia Software
---

### Post by cybrsaylr on 2014-12-12
Pithos played normal this afternoon.
Tried playing it again a few minutes ago and it won't play anything anymore.

Had an old Pithos version that stopped playing. Saw a suggestion to install the new Pithos version 1.0.1 and did so but it still won't run.

Just keep getting [error: Forbidden] messages after each song and the last song shows a message [Buffering (0%) - Error : Internal data flow error.] 
I appear to be signed in and all but it just won't play any stations set to run.

Anyone know what the problem is, or how to get Pithos up and running again?

---

### Post by QIII on 2014-12-12
Do you get any errors if you run it from the terminal?

```
pithos
```

Try something good like Flogging Molly! :evil:

---

### Post by cybrsaylr on 2014-12-12
When I run it from terminal it opens, then shows a whole host of the same errors shown below in terminal.
Here are a few of them:

```
ERROR - pithos:on_gst_error:660 - Gstreamer error: Forbidden, gstsouphttpsrc.c(1200): gst_soup_http_src_parse_status (): /GstPlayBin:player/GstURIDecodeBin:uridecodebin5/GstSoupHTTPSrc:source:
Forbidden (403), URL: [http://mediaserver-sv5-rt-1.pandora.com/access/2635438931895460520.mp4?version=4&lid=702048874&token=CXmgO4H8N6OYYqfKGU8QtFRkMx4GcHxoxjujYlzUgtzFMjAE3eWtPJJw9p8MXAZqsp3lQ%2BjxzIw4FqX4tkFEk%2BCqN9gGCAuHc5cXqy2LcDCRC24mrGp2Edo78oxScQzw2Ttg35jCswBNUXbnC3ekgnV7vZQltgclHHzA9o9s7kTt2vD5jcl6zOzIqTpkjjjLMGr2c1pAb1gt1lxoAFk%2FtkOsL%2Fp2JhLJRzGirQt0RkX5FaeNq%2BbPdc4gqNYCvUukzzMvMM2CHlTdQbekjSzyJ0pnjXvLueSl6iL22iVw%2Bd5lZ4xC9fxwJy3EuMHxAf%2F%2BnizbzaMMN%2FL8BqXsN95ihEhf4BqADIKmlCe%2BFjkD6o7CaMPHIuVaz1PID3ejMGBMBenUY8E4v%2Flbbj1g%2B8bIwvpgORNw%2FGGZoruCUSiEBvZ5IUPfbgB46aRlKzL3X%2BVVhflx3wKxvdjD%2BZkvKtLXzSYuNnZRaT35yq7aPSwOamLDTgq0esSW2rnEtQ19O3M30vbK6PHuw7T89uXplD1NM1KqbyEsWFnj%2BY3FDNjKRwsda4xIgqFVBiyL2vuCIL1ObsgHtXlSirc7SGJhGPRIkiTKadBZ8JyO](http://mediaserver-sv5-rt-1.pandora.com/access/2635438931895460520.mp4?version=4&lid=702048874&token=CXmgO4H8N6OYYqfKGU8QtFRkMx4GcHxoxjujYlzUgtzFMjAE3eWtPJJw9p8MXAZqsp3lQ%2BjxzIw4FqX4tkFEk%2BCqN9gGCAuHc5cXqy2LcDCRC24mrGp2Edo78oxScQzw2Ttg35jCswBNUXbnC3ekgnV7vZQltgclHHzA9o9s7kTt2vD5jcl6zOzIqTpkjjjLMGr2c1pAb1gt1lxoAFk%2FtkOsL%2Fp2JhLJRzGirQt0RkX5FaeNq%2BbPdc4gqNYCvUukzzMvMM2CHlTdQbekjSzyJ0pnjXvLueSl6iL22iVw%2Bd5lZ4xC9fxwJy3EuMHxAf%2F%2BnizbzaMMN%2FL8BqXsN95ihEhf4BqADIKmlCe%2BFjkD6o7CaMPHIuVaz1PID3ejMGBMBenUY8E4v%2Flbbj1g%2B8bIwvpgORNw%2FGGZoruCUSiEBvZ5IUPfbgB46aRlKzL3X%2BVVhflx3wKxvdjD%2BZkvKtLXzSYuNnZRaT35yq7aPSwOamLDTgq0esSW2rnEtQ19O3M30vbK6PHuw7T89uXplD1NM1KqbyEsWFnj%2BY3FDNjKRwsda4xIgqFVBiyL2vuCIL1ObsgHtXlSirc7SGJhGPRIkiTKadBZ8JyO), 15
ERROR - pithos:on_gst_error:660 - Gstreamer error: Forbidden, gstsouphttpsrc.c(1200): gst_soup_http_src_parse_status (): /GstPlayBin:player/GstURIDecodeBin:uridecodebin6/GstSoupHTTPSrc:source:
Forbidden (403), URL: [http://mediaserver-sv5-rt-1.pandora.com/access/5918838495984260784.mp4?version=4&lid=702048874&token=CXmgO4H8N6OYYqfKGU8QtFRkMx4GcHxoxjujYlzUgtwdA6pE%2FX8ffZTahNmTNMZqpfq%2Fd2KKzYEo0091eZCjfw5RKxupmgSKoMdalpnXigymE%2BXmoXbIXo6VCXRyLpxdoL163cqT7ZDA0Xc0HUWw%2BpWNCnxRCyhSjzdfqBzfkn%2FvFIW0QxRWhZV%2FMdzU6VWhx72eX6Zq4jiUtB7T2sZSiAG8FRyZw3t0bjeUmki5xxp5n7aEua0uaKEhJ2J4NctTbMztULVxcew4JVZx68DSkthHhVvP2SAhWef%2FJdAD8JUbve%2FN0REmsSlVyB%2FbhSf6QvGBcOzTlZ3%2BoNKtqHUzxkwMQy4OxLauBdGiK9NvCBE72pf7jf45y%2BMTiQPIaN0jINqsc4trcTjLcxsHWIf0YXe2boFUQbB2GX8qSX%2B6WfoWmzcSQXrcgbQmZkb3KhTU1VV1FK%2FcyEQHUhBwujCtsWgCCtghyKToCTaQ6X8prGAETVZuYWevWF1fKWF2fwumC0ivrUusEqwsY4yskjWwz4VUvnmL2%2F1xeuy1hGPnYsl0xNrfESSINjIKmXHpXDn50IMdlcUPI%2BBuFNBxSWkXqx9g7EuUSRNTifJzRR65YRc%3D](http://mediaserver-sv5-rt-1.pandora.com/access/5918838495984260784.mp4?version=4&lid=702048874&token=CXmgO4H8N6OYYqfKGU8QtFRkMx4GcHxoxjujYlzUgtwdA6pE%2FX8ffZTahNmTNMZqpfq%2Fd2KKzYEo0091eZCjfw5RKxupmgSKoMdalpnXigymE%2BXmoXbIXo6VCXRyLpxdoL163cqT7ZDA0Xc0HUWw%2BpWNCnxRCyhSjzdfqBzfkn%2FvFIW0QxRWhZV%2FMdzU6VWhx72eX6Zq4jiUtB7T2sZSiAG8FRyZw3t0bjeUmki5xxp5n7aEua0uaKEhJ2J4NctTbMztULVxcew4JVZx68DSkthHhVvP2SAhWef%2FJdAD8JUbve%2FN0REmsSlVyB%2FbhSf6QvGBcOzTlZ3%2BoNKtqHUzxkwMQy4OxLauBdGiK9NvCBE72pf7jf45y%2BMTiQPIaN0jINqsc4trcTjLcxsHWIf0YXe2boFUQbB2GX8qSX%2B6WfoWmzcSQXrcgbQmZkb3KhTU1VV1FK%2FcyEQHUhBwujCtsWgCCtghyKToCTaQ6X8prGAETVZuYWevWF1fKWF2fwumC0ivrUusEqwsY4yskjWwz4VUvnmL2%2F1xeuy1hGPnYsl0xNrfESSINjIKmXHpXDn50IMdlcUPI%2BBuFNBxSWkXqx9g7EuUSRNTifJzRR65YRc%3D), 15
WARNING - pithos:get_playlist:543 - Too many gstreamer errors. Not retrying
```

---

### Post by QIII on 2014-12-13
Is this happening just on one "station"?

---

### Post by cybrsaylr on 2014-12-13
Happens on all 3 stations I have.

---

### Post by QIII on 2014-12-13
Is this a free Pandora account?  The error you are getting is a permission failure accessing the resource on the web.

---

### Post by cybrsaylr on 2014-12-13
Yes this is the free Pithos/Pandora account I've used for a couple years with no problems.

---

### Post by QIII on 2014-12-13
OK.  Try to just access one of those urls directly and see if it will play in your browser.  You'll probably have to have Pithos running.  Just hit the pause button and then try to access the resource directly.

---

### Post by cybrsaylr on 2014-12-13
Discovered when clicking on Pithos version 1.0.1 on what looks like a 'lightbulb' icon, just to the left of the station title bar, this opens Firefox browser and plays my station on Pandora in FF! 

But I prefer to run it in Pithos which no longer will run.


PS: and when it stated playing Pandora gave me a message telling me to enjoy my one hour of uninterrupted music!

---

### Post by QIII on 2014-12-13
OK.  Trying to find bug reports in between looking through other posts here.  Someone else may chime in here if I don't get back to this before long.


Edit:  Did you install this from the repo or from a PPA?

---

### Post by cybrsaylr on 2014-12-13
OK thanks for the help.

Really enjoy Pithos and hope it didn't get messed up!

---

### Post by cybrsaylr on 2014-12-13
Well an hour later Pandora stopped playing with Firefox and gives this message when trying to switch to other stations:
> We're sorry, but we can't find any more music to play on your station right now. Try switching stations. 

---

### Post by QIII on 2014-12-13
Well, that really sounds like it's on the Pandora end.

I'm looking for a Pandora forum at the moment, but what I am finding is a bunch of junk.

Edit:  There's [this]("http://help.pandora.com/"), but I don't see a forum...

---

### Post by cybrsaylr on 2014-12-13
Yep Pandora keeps saying it's their fault. Hope they fix it because I liked them.

Using Last FM right now. Forgot the reason I dumped them for Pithos long time ago.

Are there any other good free streaming radio sites out there?

---

### Post by cybrsaylr on 2014-12-14
Well last evening Pithos 1.0.1 started working again!
Was getting messages from Pithos/Pandora saying they were having problems, so hopefully they are resolved. It has been running fine all day today. 

While Pithos was down I did a little searching for other music sources and installed Vagalume but it would not play either! Vagalume acted as strange as Pithos which was down. Have used Vagalume in the past before switching to Pithos and was surprised Vagalume, a Last FM client would not play. Last FM played using FireFox but the sound quality was not as good as Pandora/Pithos. Listened to Pandora for awhile using Firefox than suddenly it would not play either in Firefox! Don't know why? However Pandora played fine using  Opera beta 27.0 version browser. 

FWIW Opera has been one of my favorite browsers going back to Opera 3.5 days. Opera beta 27.0 version in spite of being a beta version, runs nice and is very fast. In fact believe it is faster than Chrome, or at least it appears faster.

---

### Post by cybrsaylr on 2014-12-14
Since using Opera, Ubuntu updates auto updates to the latest beta versions of Opera....it auto updated from Opera beta 26 to beta 27 version a couple days ago.

---

### Post by cybrsaylr on 2014-12-16
Pithos and Pandora went down again!

Keep getting these messages again:
> We've encountered an error. Sorry, it's our fault. Please click 'reload' to continue listening.
 Reload

When attempting to reload, the messages just keep repeating.

---

### Post by cybrsaylr on 2014-12-18
FWIW Pithos continues to run very erratically, at least for me.
Right now Pithos is down again. Was running yesterday then went down late afternoon and is still down now. Pandora play through my browsers either. However when Pithos does play there are no commercials and I'm not a paid subscriber. Another thing, when I pause Pithos now it won't restart when I unpause it. Pithos just keeps showing the above error messages.

Found Jango and use Jango playing in Firefox when Pithos is down. Jango has a nice selection of music also.

---

