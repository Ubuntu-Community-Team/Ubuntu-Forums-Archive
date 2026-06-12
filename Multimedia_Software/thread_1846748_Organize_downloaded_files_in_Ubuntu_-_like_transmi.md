---
title: "Organize downloaded files in Ubuntu - like transmission for mac os x"
date: 2011-09-19
forum: Multimedia Software
---

### Post by davidcampbell on 2011-09-19
I would like som help organizing my downloaded files.

I used to use transmission for mac for my torrent downloads, where i could create "groups" with rules. There seems to be nothing that will help me do that. For example.

i want to download an episode of a tv show and i want the file to be downloaded to
media/tv shows/name of show 1/season x/

in transmission for mac this is possible because i can create a group called "name of show 1"

it is possible to apply a label in for example utorrent. The problem comes when i want to do the same for "name of show 2" and i want it to be downloaded to

media/tv shows/name of show 2/season x/

or if i want to download an application to /media/software/category x/

Labels only seem to work if everything is to be downloaded to a folder directly under the parent chosen folder and not in subfolder/subfolder..

I transmission it is possible to create rules. for instance if i add a rule that says "any download including the name "what" is supposed to be put in the directory /some/where/, and then I add a download with the name "what.ever", it will automatically be downloaded to /some/where/.

what I need is something that will help me move or automatically download all different categories of files to whatever folder i want so I don't have to move everything after download completion. Does anyone know of a way?

---

### Post by haqking on 2011-09-19
> **davidcampbell said:**
> I would like som help organizing my downloaded files.

I used to use transmission for mac for my torrent downloads, where i could create "groups" with rules. There seems to be nothing that will help me do that. For example.

i want to download an episode of a tv show and i want the file to be downloaded to
media/tv shows/name of show 1/season x/

in transmission for mac this is possible because i can create a group called "name of show 1"

it is possible to apply a label in for example utorrent. The problem comes when i want to do the same for "name of show 2" and i want it to be downloaded to

media/tv shows/name of show 2/season x/

or if i want to download an application to /media/software/category x/

Labels only seem to work if everything is to be downloaded to a folder directly under the parent chosen folder and not in subfolder/subfolder..

I transmission it is possible to create rules. for instance if i add a rule that says "any download including the name "what" is supposed to be put in the directory /some/where/, and then I add a download with the name "what.ever", it will automatically be downloaded to /some/where/.

what I need is something that will help me move or automatically download all different categories of files to whatever folder i want so I don't have to move everything after download completion. Does anyone know of a way?

Transmission is the default torrent client in Ubuntu, have you tried it ? i dont know if it does what you want as i use qbittorrent and that has labels and there are many others such as deluge

---

### Post by davidcampbell on 2011-09-19
> **haqking said:**
> Transmission is the default torrent client in Ubuntu, have you tried it ? i dont know if it does what you want as i use qbittorrent and that has labels and there are many others such as deluge

Thanks for the reply. Yes I have tried transmission and also a couple of other clients but there's nothing that lets me organize with rules or labels the way transmission for mac does, with complete seperate download locations. I'll keep trying my luck but if anyone has another tip, please let me know!

---

### Post by haqking on 2011-09-19
> **davidcampbell said:**
> Thanks for the reply. Yes I have tried transmission and also a couple of other clients but there's nothing that lets me organize with rules or labels the way transmission for mac does, with complete seperate download locations. I'll keep trying my luck but if anyone has another tip, please let me know!


yeah like i said qbittorrent does, you assign a label and set a location for that label.

i think there is a label plugin for deluge also, and the linux transmission is due to have labels at some point apparently.

---

### Post by davidcampbell on 2011-09-19
> **haqking said:**
> yeah like i said qbittorrent does, you assign a label and set a location for that label.

i think there is a label plugin for deluge also, and the linux transmission is due to have labels at some point apparently.

Thanks again! I've have now checked qbittorrent and it's the same as utorrent with the posibillity to create labels. Although it is not possible to assign the labels automatically, it doesn't support subdirectories and the webversion doesn't have the option of labels. I forgot to say that the webversion was important as well. The reason is that i don't have access to the desktop of the computer thats doing the downloading so it needs to be automated.

I've tried all torrent clients in the ubuntu standard repository and havent found what i'm looking for. Anyone have any other suggestions? 

I could create a script that sorts my files and moves them to the appropriate directory after "some time". The problem is that after the torrent is moved i can't seed anymore which kind of defeats the purpose of torrents.

Does anyone know a torrent client that supports labels in webui?
any help is appreciated?


edit:sorry for the caps if anyone saw it..

---

### Post by shiraz dindar on 2011-09-21
agreed -- qbitorrent's labels are limited vs utorrent's labels in the two ways just mentioned: 

1. no subfolders. With the "append label to save path" setting enabled, say you're downloading video, and you want some to go into "Videos/Fiction" and others into "Videos/Documentaries". In uTorrent, this worked fine by specifying the labels as such, but it qBitorrent it complains that you're using special characters in the label -- thus, no subfolders.

2. no automatic labelling based on file type. This is a new'ish uTorrent feature, so I think it's understandable that it's not in qBitorrent. But it's a nice to have.

The last I tried Deluge a couple months ago, I found it had what seemed like various (possibly, conflicting) plugins to handle the above and yet I still couldn't get it to do either of the above properly. Having said functionality in plugins, it wasn't very streamlined, and I went back to qBitorrent. 

Thoughts?

---

### Post by davidcampbell on 2011-09-22
Yes! Finally
I found what I'm looking for. Since no torrent client (i know of, I might add) has support for automatic labeling and labels with subfolders, i started to check plugins for web browsers that can remotely control a torrent client. And voila! I found a genius plugin for google chrome called "Remote Transmission" -by vyrticl.
check [http://bit.ly/hP1Yi7]("http://bit.ly/hP1Yi7")
With this plugin it's possible to add labels with subdfolders and whenever you click on a torrent link, you get to choose which label to use before starting the download. And the best part is, I can keep using transmission.

*dancing*

---

### Post by haqking on 2011-09-22
> **davidcampbell said:**
> Yes! Finally
I found what I'm looking for. Since no torrent client (i know of, I might add) has support for automatic labeling and labels with subfolders, i started to check plugins for web browsers that can remotely control a torrent client. And voila! I found a genius plugin for google chrome called "Remote Transmission" -by vyrticl.
check [http://bit.ly/hP1Yi7]("http://bit.ly/hP1Yi7")
With this plugin it's possible to add labels with subdfolders and whenever you click on a torrent link, you get to choose which label to use before starting the download. And the best part is, I can keep using transmission.

*dancing*

cool, glad you got it sorted.  Please mark the thread as solved using thread tools.

cheers

---

