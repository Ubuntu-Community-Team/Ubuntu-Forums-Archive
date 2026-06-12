---
title: "Jamu movie help"
date: 2011-05-03
forum: Mythbuntu
---

### Post by raptorjr on 2011-05-03
I tried to get help on the myth mailinglist, but no one seems to know the answer.

When Jamu downloads metadata for my recordings it fails to get data for movies. It tries to find a movie inetref, and if that fails it seems that it treats the recording as a TV series. Is it possible to get Jamu to search for movies by name if inetref fails?
I have updated themoviedb.org with the correct swedish names. But that wont help if Jamu dont even try to find it.

Here is a example of The Good, The Bad, The Ugly:

No movie inetref [Den gode, den onde, den fule (1966)]
TV Series - No (fanart) for [Den gode, den onde, den fule]
TV Series - No (coverfile) for [Den gode, den onde, den fule]

/Stefan

---

### Post by ian dobson on 2011-05-03
Hi,

I'm using imdb.py to scan my videos and I have found out that if I name the files exactly the same as the movie, followed by the year it finds the information correctly.

Go to [www.imdb.com](www.imdb.com), find the exact title and rename the file to that name, it doesn't always work but for me it worked for about 90% of my films.

Regards
Ian Dobson

---

### Post by raptorjr on 2011-05-04
Hmm, i guess i have to do that. Would have liked to use Jamu for everything since it uses open databases that i can add info to. And since Jamu should be able to get both movies and series metadata i thought it was possible to get it to work for recorded movies also.

---

### Post by ian dobson on 2011-05-04
Hi,

Just change your file titles so that they are exactly the same a in imdb, that might do it.

Regards
Ian Dobson

---

