---
title: "mediatomb folder view"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by jacc1234 on 2007-07-02
I am trying to setup mediatomb as a replacement for my soon to be disabled twonky server but I am running into a problem. The issue is that I like to organize my media using directories instead of tags. Twonky has a "folder" view where it will let me see my media just as it is on my computer. Twonky also has a "PC Directory" but i have to click through /home/name/media/mp3 instead of just viewing the /mp3 folder. Is there anyway to change this?

Thanks,
Jacc1234

---

### Post by jacc1234 on 2007-07-03
bump

---

### Post by specvthis on 2008-01-02
bump

---

### Post by specvthis on 2008-01-02
Aha.  I was perusing the Mediatomb forums over on sourceforge and came across htis snippet of code that worked wonderfully.  I have my tv shows set up in the directory structure:

Tv Show Name->Season Number->blah.avi

function addVideo(obj)  
{  
var chain, show, season;  
var location = obj.location.replace(/_/g," ").split('/');  
 
chain = new Array('Video');  
 
if (location.length > 3) {  
chain.push(location[location.length-3]);  
if (location.length > 4) { chain.push(location[location.length-2]); }  
}  
 
addCdsObject(obj, createContainerChain(chain));  
}  

Using that as my import video in the import.js file worked magically!

---

### Post by 4wding on 2008-01-03
I just wrote a slightly more generic version of this method which replicates my directory structure exactly at the Mediatomb root level. I also added 'Index', to the front of all the other Array() creation statements for other containers so that ALL of the Mediatomb created elements are grouped in the 'Index' container.

function addDirectoryView(obj)
{
    var chain = new Array();
    var location = obj.location.split('/');

    // location is in the form of /mnt/MEDIA/TV Shows/Heroes/Season 1/episode.avi
    // this should add TV Shows + Heroes + Season 1 to the path of MEDIA
    for (x=3;x<location.length-1;x++)
    {
      chain.push(location[x]);
    }
  
    addCdsObject(obj, createContainerChain(chain));
}

This method is then called for ALL objects.

---

### Post by fulmitz on 2008-02-18
Sounds like what I've been looking for, thanks.  I am however an extreme noob when it comes to Linux and Ubuntu.  What file do I edit and where do I place the piece of code?  Can I just copy and paste it as is?  Thanks,

fulmitz

---

