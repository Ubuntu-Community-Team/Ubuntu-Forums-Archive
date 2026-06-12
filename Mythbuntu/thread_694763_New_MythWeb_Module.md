---
title: "New MythWeb Module"
date: 2008-02-12
forum: Mythbuntu
---

### Post by Stevieo85 on 2008-02-12
Hi All,

I have a created a new module for MythWeb, the module allows you to upload m3u files, you can then select that m3u file and use it to create a playlist for mythmusic.

There is a few limitations at present with the module, basically the m3u file has to be modified so that it has only the path to the mp3 file from the mythmusic directory, this is however easily completed using the search replce feature of any text editor.

for example i have the line in an m3u file
#EXTINF:0,03 - Who's Got A Match.mp3
..\..\..\Copy of newMusic\Biffy Clyro\Puzzle\03 - Who's Got A Match.mp3
and i use the find replace to find ..\..\..\Copy of newMusic\ and replace with nothing.

I hope to improve the module so that it will show you the path to the mp3 and allow you to specify what part should be removed.

I would like to offer this to others to use if you think you would find it useful, as a start for me to get involved with the open source community for this project...I hope to get involved with possibly writing a new frontend for mythmusic eventually.

What I am here asking for is a bit of advice on how to get involved and how to package what i have coded so that it can be shared.

Thanks for reading the long post. And any other comments about what i have described and whether you think it will be usefull will be appreciated as well.

---

