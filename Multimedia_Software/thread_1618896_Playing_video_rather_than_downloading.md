---
title: "Playing video rather than downloading ?"
date: 2010-11-11
forum: Multimedia Software
---

### Post by BADGER.BRAD on 2010-11-11
Hello All,

Can anyone help with this problem ( something simple no doubt) If I try to download a video for later use Ubuntu streams the video instead. How can I get around this?

Many thanks all

Brad

---

### Post by cotcot on 2010-11-11
It would be useful that you clarify your question. How do you try to download video ? And from what source ?
Check [[COLOR="Red"]this[/COLOR]]("http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl") (supposing you want to download something from youtube) or [[COLOR="Red"]this[/COLOR]]("http://www.hermann-uwe.de/blog/download-videos-from-youtube-google-video-and-others-using-linux").

---

### Post by BADGER.BRAD on 2010-11-11
Hello cotcot,

Thanks for the reply much appreciated,I am trying to download various documentaries from this site 
[http://www.kolibka.com/2.html](http://www.kolibka.com/2.html) In windows I could do this by simpley clicking on the download link If I try this with Ubuntu it starts to play the video. Which is of no real use to me.Any ideas

Many Thanks Brad

---

### Post by SeijiSensei on 2010-11-11
That URL times out for me.

What if you right click on the download link?  You should see an option to save the file.

---

### Post by mc4man on 2010-11-11
While the dl is a bit slow (at least from here) a 
wget url
works ok - get url from r. click - copy link location

---

### Post by BADGER.BRAD on 2010-11-12
Hello,

Forgive my Windoze infested brain but what does wget url mean and how do I do it ( I understand url bit) seems very strange as I could never get Windoze to play the thing and the only option was to download then play later.

---

### Post by mc4man on 2010-11-12
> what does wget url mean 
Open a terminal type wget, hit spacebar and paste or type url to video, press enter

So picking a video (from the page off of top of list on left - basically I don't understand a word on the site) and r. click 'copy link location' would give this

[http://www.kolibka.com/download.php?mid=2238](http://www.kolibka.com/download.php?mid=2238)

So in a terminal as ex.
> doug@doug-laptop:~$wget [http://www.kolibka.com/download.php?mid=2238](http://www.kolibka.com/download.php?mid=2238)

--2010-11-12 14:46:02--  [http://www.kolibka.com/download.php?mid=2238](http://www.kolibka.com/download.php?mid=2238)
Resolving [www.kolibka.com](www.kolibka.com)... 193.200.15.181
Connecting to [www.kolibka.com|193.200.15.181|:80](www.kolibka.com|193.200.15.181|:80)... connected.
HTTP request sent, awaiting response... 303 REDIRECT
Location: [http://treasure.kolibka.com/-users/petkan/Carl%20Sagan's%20COSMOS%20(BozoMaster)/Carl.Sagan's.COSMOS(1980)_01_The.Shores.of.the.Cosmic.Ocean-BozoMaster.avi](http://treasure.kolibka.com/-users/petkan/Carl%20Sagan's%20COSMOS%20(BozoMaster)/Carl.Sagan's.COSMOS(1980)_01_The.Shores.of.the.Cosmic.Ocean-BozoMaster.avi) [following]
--2010-11-12 14:46:03--  [http://treasure.kolibka.com/-users/petkan/Carl%20Sagan's%20COSMOS%20(BozoMaster)/Carl.Sagan's.COSMOS(1980)_01_The.Shores.of.the.Cosmic.Ocean-BozoMaster.avi](http://treasure.kolibka.com/-users/petkan/Carl%20Sagan's%20COSMOS%20(BozoMaster)/Carl.Sagan's.COSMOS(1980)_01_The.Shores.of.the.Cosmic.Ocean-BozoMaster.avi)
Resolving treasure.kolibka.com... 193.200.15.181
Reusing existing connection to [www.kolibka.com:80](www.kolibka.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 737576960 (703M) [video/x-msvideo]
Saving to: `download.php?mid=2238'

As mentioned the dl was a bit slow, around 250K/s, took 40 m9ns or so.

Aterwards renamed file to  The Shores of the Cosmic Ocean.avi  -

---

### Post by BADGER.BRAD on 2010-11-12
Thanks very much mc4man all is working now, much appreciated and thanks for your time everyone.

Brad

---

### Post by BADGER.BRAD on 2010-11-13
I ask very quickly where do the files go ? I've done a search for them but cannot find them.

Thanks all

Brad

---

