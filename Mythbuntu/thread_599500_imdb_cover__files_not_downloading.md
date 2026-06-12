---
title: "imdb cover  files not downloading"
date: 2007-11-01
forum: Mythbuntu
---

### Post by rosarch on 2007-11-01
I am trying to download film covers in mythvideo

I am able to get the imdb data and it says it has found a cover but I cant find the file anywar and it doesnt display when when selecting a video to play. I have run a locate on the server and the file cant be found.

I have run the script that seems to be running and it returns a valid url with the image, is this menat to download it or do you have to do this yourself?

/usr/share/mythtv/mythvideo/scripts/imdb.pl -P 0890870

returns

[http://www.impawards.com/2007/posters/saw_iv.jpg](http://www.impawards.com/2007/posters/saw_iv.jpg)

Cheers
Rosarch

---

### Post by axelsvag on 2007-11-01
How exactky do you do when you "download film covers in mythvideo"? I presume you go into the menu "filmmanager" in the frontend and there put in the imdb number you find on the internetmanually.

---

### Post by rosarch on 2007-11-01
I have tried it both ways in the 'Filmmanger' inserting the imdb number manually and searching for it. When the info comes back it says it has a cover <title>.jpeg but this cover is not viewable when browsing videos. Should this download and link automatically?

Cheers

---

### Post by axelsvag on 2007-11-01
Yes and you should see some information in the "filmmanger" about for example the year it was made and the  director. Then, when you go back to watch the video you should see information about the movie.

---

### Post by rosarch on 2007-11-01
I know that - as I said in the original post I can see the data, the issue I have is with 'film covers' in the 'filmmanager' it references a film cover however this is not displayed when actually browsing the films. So far I have been manually downloading and linking pictures.

---

### Post by axelsvag on 2007-11-01
Can you give me an imdb number you have used and not worked and I will try to see if it is the same for me?

---

### Post by rosarch on 2007-11-01
Sure can - one from the original post '0890870'

Cheers

---

### Post by axelsvag on 2007-11-02
I put in the 890870 manually in the "filmmanager" and went back to media librarary/watch movies and there the Saw iV was with cover and all. So the IMDB number seems to work. What version of mythbuntu do you use? The RC or FR or upgrade from an existing version?

---

### Post by toorima on 2007-11-11
check the permissions on the directory that holds the movie posters, probably ~/.mythtv/MythVideo

---

