---
title: "Problems reading mp3-files on a Windows domain"
date: 2009-10-20
forum: Multimedia Software
---

### Post by nixnewbie on 2009-10-20
After Windows Vista crashed on time to many (yes, I know, I know) I decided to try Linux for the first time. I have now installed Ubuntu v 9.04 (real smooth installation) on my computer and everything seems to work fine. My problem is that not only was I stupid enough to run Windows Vista, I also installed a Windows Server. A proper Windows Network, with a domain controller and all, running Windows Server 2003. I use the server basically as a file server, storing music and pictures on a reasonably safe place.

I was under the impression that it was really, really hard to get a Linux computer to access the files on a Windows Network. I was wrong, to my relief I could just click my way through to my "network places" and mount the shares.

So basically everything looked fine for a while. Then of course I wanted to start listening to the music stored on my server. I started Rhythmbox (0.12.0) and although it can "see" the mounted disks it can not read any files on them. Ie I can click my way up and down in my directory tree and try to play/add the files but no luck.

By now you think, well that's easy, you must just download the right codec or something. Or you must do what you do not want, ie get down and dirty with networking details and slay the domain-dragon. Well, maybe. The thing is if I run the movie application "Totem Movie Player 2.26.1" it can easily play the very same files that Rhythmbox failed to play. And we are talking about normal mp3-files, I do understand that I am missing a wma-codec.

What gives? The error message from Rhythmbox is simple:
"Could not open resource for reading."

And that of course makes me afraid that it is something really tricky, just because "Movie Player" can play the very same file, from the very same mount?

Has anyone encountered something like this before?

---

