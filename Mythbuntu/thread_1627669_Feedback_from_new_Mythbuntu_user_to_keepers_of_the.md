---
title: "Feedback from new Mythbuntu user to keepers of the website"
date: 2010-11-21
forum: Mythbuntu
---

### Post by kyphos on 2010-11-21
I'm new to Ubuntu and Mythbuntu. I downloaded the 10.04 Mythbuntu LiveCD a couple weeks ago, and am still struggling to get the system working reliably. 

Here are a couple of suggestions for the keepers of the Mythbuntu package and the mythbuntu.org website that may lessen the learning curve for other newcomers.

1) Configure the Mythbuntu package so that the Update Manager application automatically obtains the appropriate AutoBuilds (or whatever they are called now). See [http://www.mythbuntu.org/article/7](http://www.mythbuntu.org/article/7)
After installing from the LiveCD, I ran Update Manager a couple of times, thinking it was a good idea to obtain whatever bug fixes had been issued since the 10.04 LiveCD package was assembled.  Little did I know that out-of-the-box,  Update Manager doesn't actually update the mythtv software.

I've been chasing my tail the last two weeks troubleshooting issues that, as it turns out, had already been fixed. I thought I had the 'latest' versions of software, since I had run Update Manager. But I didn't. Entirely my fault, of course, for not having the necessary domain knowledge to reconfigure Update Manager in the first place.

2) Augment the instructions found at [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) to clearly explain what a _neophyte_ user needs to do to update his/her installation. In particular, write a detailed prescription under the existing heading "[COLOR=Blue]**Install the Mythbuntu-repos package**[/COLOR]". At present, that topic simply downloads a file named **mythbuntu-repos.deb**. Like many users, my Mythbuntu system feeds a TV screen 12 feet away. It's hard to read browser pages, has no printer, and is generally not conducive to troubleshooting & online research. I use my MacBook to google the web, read forum articles, print helpful articles, etc etc.  When I clicked the link to install the repos package, the .deb file got downloaded into my Safari download folder. Not much help, I'm afraid. None of my handy Mac utilities could open it. It was not at all clear what to do next.  More time wasted searching the forums...

I think it would be more helpful for neophyte users if the /repos page on the mythbuntu.org website provide step-by-step instructions on accessing and activating the needed repository, starting with "Launch the Mythbuntu Control Centre (MCC) on your Myth system".  

3) The latest Mythbuntu News article (as of 21 Nov 2011) indicates that there are now two repositories of updates, one for MythTV and one for Mythbuntu.  It's not clear to me whether installing the mythbuntu-repos.deb file with the Package Installer gets them both or only the Mythbuntu fixes.  If additional steps are required to access the MythTV-updates repository, that should be detailed on [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) webpage.

4) My last suggestion in this area would be a little ReadMe file (left on the desktop after the Mythbuntu installation completes) providing guidance on 'best practices' for the care and feeding of one's shiny new MythTV system. For example, I'm now wondering whether I should stay with the 0.23 stream that was in Mythbuntu 10.04,  upgrade to 0.23.1, make the leap to 0.24, etc. (comments welcome).   Such a ReadMe could also mention the importance of regular backups, the daily MySQL optimize job, and other topics new users should become familiar with. I'm sure someone in the community has written just such a tutorial, though I haven't found it yet.  Leaving it on right on the desktop would really help neophytes get up the learning curve.

---

### Post by tgm4883 on 2010-11-21
> **kyphos said:**
> I'm new to Ubuntu and Mythbuntu. I downloaded the 10.04 Mythbuntu LiveCD a couple weeks ago, and am still struggling to get the system working reliably. 

Here are a couple of suggestions for the keepers of the Mythbuntu package and the mythbuntu.org website that may lessen the learning curve for other newcomers.

1) Configure the Mythbuntu package so that the Update Manager application automatically obtains the appropriate AutoBuilds (or whatever they are called now). See [http://www.mythbuntu.org/article/7](http://www.mythbuntu.org/article/7)
After installing from the LiveCD, I ran Update Manager a couple of times, thinking it was a good idea to obtain whatever bug fixes had been issued since the 10.04 LiveCD package was assembled.  Little did I know that out-of-the-box,  Update Manager doesn't actually update the mythtv software.

I've been chasing my tail the last two weeks troubleshooting issues that, as it turns out, had already been fixed. I thought I had the 'latest' versions of software, since I had run Update Manager. But I didn't. Entirely my fault, of course, for not having the necessary domain knowledge to reconfigure Update Manager in the first place.


Can't be done. I really would like to do that, but am unable to get the mythbuntu-repos package into the Ubuntu repositories. Sorry :(

> **kyphos said:**
> 
2) Augment the instructions found at [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) to clearly explain what a _neophyte_ user needs to do to update his/her installation. In particular, write a detailed prescription under the existing heading "[COLOR=Blue]**Install the Mythbuntu-repos package**[/COLOR]". At present, that topic simply downloads a file named **mythbuntu-repos.deb**. Like many users, my Mythbuntu system feeds a TV screen 12 feet away. It's hard to read browser pages, has no printer, and is generally not conducive to troubleshooting & online research. I use my MacBook to google the web, read forum articles, print helpful articles, etc etc.  When I clicked the link to install the repos package, the .deb file got downloaded into my Safari download folder. Not much help, I'm afraid. None of my handy Mac utilities could open it. It was not at all clear what to do next.  More time wasted searching the forums...

I think it would be more helpful for neophyte users if the /repos page on the mythbuntu.org website provide step-by-step instructions on accessing and activating the needed repository, starting with "Launch the Mythbuntu Control Centre (MCC) on your Myth system".  


I could augment the instructions on a separate page, but if you don't already know that what to do with a .deb file (or even try just double clicking on it) i'm not sure you would click through to another page for that information. Even if I did, the instructions would simply say 1) Download file, 2) Double click it

> **kyphos said:**
> 
3) The latest Mythbuntu News article (as of 21 Nov 2011) indicates that there are now two repositories of updates, one for MythTV and one for Mythbuntu.  It's not clear to me whether installing the mythbuntu-repos.deb file with the Package Installer gets them both or only the Mythbuntu fixes.  If additional steps are required to access the MythTV-updates repository, that should be detailed on [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) webpage.


The first sentence from [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) says
```
The Mythbuntu team provides a package (mythbuntu-repos) to allow users to easily activate additional update repositories for software shipped with Mythbuntu.
```

Combine that with the FAQ and Common uses sections from the same page and I am unsure how you do not know that the mythbuntu-repos package gives you the ability to activate either repository. Keep in mind that when you do install the mythbuntu-repos package, debconf specifically asks you about each repository and whether you want to activate it or not.

> **kyphos said:**
> 
4) My last suggestion in this area would be a little ReadMe file (left on the desktop after the Mythbuntu installation completes) providing guidance on 'best practices' for the care and feeding of one's shiny new MythTV system. **For example, I'm now wondering whether I should stay with the 0.23 stream that was in Mythbuntu 10.04,  upgrade to 0.23.1, make the leap to 0.24, etc.** (comments welcome).   


Covered in the FAQ section on [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

> **kyphos said:**
> 
Such a ReadMe could also mention the importance of regular backups, the daily MySQL optimize job, and other topics new users should become familiar with. I'm sure someone in the community has written just such a tutorial, though I haven't found it yet.  Leaving it on right on the desktop would really help neophytes get up the learning curve.

Ultimately this is a media center. I'll look into including some sort of Best Practices type of document, but in the end it is still up to the user to know the basics about backups and such. And where would I put this document? Surly not on the desktop, the very place you said you couldn't read things on?

I really would like to help, I just think the things you are asking about is overly basic.

---

