---
title: "downloading rapidshare premiun"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by franar on 2009-04-01
hi, this is my first time in the forums, with a subject very explained in other places but, there is not way for me to work, 
the problem as a mencionated is getting a good downloading manager to work with rapidshare (like win flasget), a have read about aria working with flasgot, but I have found some configuratios all differents but any works good to me. I see some thread are so old so I think it could be the problem, so i like someone tell what to use in some way recient.....

sorry for the english and thanks in advance

Fran

---

### Post by steeleyuk on 2009-04-01
[This script]("http://rapidshare.com/files/121995350/modrapi-1.3-notfullytested.tar.gz") works very well but its command line only.

More instructions on using it [here]("http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html").

---

### Post by franar on 2009-04-01
> **steeleyuk said:**
> [This script]("http://rapidshare.com/files/121995350/modrapi-1.3-notfullytested.tar.gz") works very well but its command line only.

More instructions on using it [here]("http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html").

thanks I've heard of this from the terminal, but i did see as an option, but if that is the only way to no log in windows i guess i must try it.....

the bad with this option is that you must type the rapidshare link but when the links are 40 or more what happends? the scripts controls a part of the links typed or all the typed links start to download in the same time???

---

### Post by steeleyuk on 2009-04-01
You can import a file.

Enter your rapidshare links into a text file, one line per line. Then at the prompt type **./modrapi file filename.txt**. It should then tell you thats its imported X amount of links. Then run **./modrapi download** and it'll use wget to download each file at a time.

---

### Post by franar on 2009-04-01
excelent, i'm working right now, so i can't try but it will be the first to do tonight, 

tks steeleyuk ;)

---

### Post by franar on 2009-04-02
so bad, when i extract the compress file I can't place in the adress /usr/bin because this is read only, so the next step can be done because the command "try" to use the file in /usr/bin....

help please

---

### Post by psykro on 2009-04-06
> **franar said:**
> so bad, when i extract the compress file I can't place in the adress /usr/bin because this is read only, so the next step can be done because the command "try" to use the file in /usr/bin....

help please

franar, no need to extract to /usr/bin, simply extract the modrapi script anywhere, open a terminal, go to the location of the modrapi script and enter ```
./modrapi
``` to run it.

---

### Post by castronovab on 2009-04-17
The eaiesty way I found to download premium links in Rapidshare or any other site u are a member to is to install Flashget in WIne and download it that way....its less steps and it works

---

### Post by kaloi2 on 2009-05-05
Firefox's plugin DownloadThemAll also support rapidshare premium account. Login into rapidshare account>Setting>tick Direct Download.

Right click rapidshare link, pick download with DownloadThemAll and you done.

---

### Post by danjh2705 on 2009-05-15
if you want a gui download manager i recommend jDownloader (cross platform java script) it will download form any hosting site and allows association of archive passwords and automated extraction :)

for commandline I use modrapi which is also good.

---

### Post by enli on 2009-07-09
USDownloader also works - but with wine.

---

