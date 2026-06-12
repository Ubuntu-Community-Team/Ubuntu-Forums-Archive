---
title: "Can we get real MythTV support for ubuntu?  mythbuntu is too dumbed down."
date: 2008-01-24
forum: Mythbuntu
---

### Post by the Goat on 2008-01-24
A lot of work went into Mythbuntu and I'm sure many people like it.  But for serous users mythbuntu just gets in the way.

For instance Mythbuntu Control Centre is way more confusing then just using apt-get from the command line for the vast majority of the things it does.  And it automatically enables things that I don't want.  Like the ugly mythbuntu start-up and shut-down screens.

Also the mythbuntu install scripts don't work correctly through a proxy connection.  This shows sloppy coding practice and a lack of testing.

And why is somebody trying to hide the real mythtv programs from the user.  The fake mythtv-setup drives me crazy.  It automatically starts up mythbackend when I exit mythtv-setup.  Who thought that would be a good idea?

These are only some of the problems found in mythbuntu.

I know people are going to be upset with my post.  They will say nobody is forcing me to use mythbuntu, I should do it myself and quit complaining.  But the fact is that the mythtv support for ubuntu 7.04 was perfect.  It was faster to setup and easier to learn.  All I want to to have mythtv supported like it was in 7.04 along with mythbuntu.

---

### Post by tgm4883 on 2008-01-24
Yep, here it comes.

If you don't like it, then don't use Mythbuntu.  There it has been said.

But seriously, why don't you just apt-get install it like you did in 7.04?  It is still in the repos.  Guess you overlooked that on you way to posting this rant huh.

---

### Post by the Goat on 2008-01-24
> **tgm4883 said:**
> Yep, here it comes.

If you don't like it, then don't use Mythbuntu.  There it has been said.

But seriously, why don't you just apt-get install it like you did in 7.04?  It is still in the repos.  Guess you overlooked that on you way to posting this rant huh.

No I didn't over look that at all.  I am asking for the apt-get method to be officially supported in parallel to the mythbuntu method.  Right now in the official MythTV Gusty documentation it tells you to install mythbuntu ([link](https://help.ubuntu.com/community/MythTV_Gutsy)).  That is the only option presented to the user.  The core of my rant is that it is a mistake to present mythbuntu as the sole MythTV solution on Ubuntu.

---

### Post by superm1 on 2008-01-25
Here's the thing.  It's an open project.  If you have support missing in particular areas (eg proxy support), file bugs in those areas.  

If you think that the documentation is lacking in other methods to do MythTV on Ubuntu, add another section and link to it in the documentation.  It's a wiki, you're able to edit things there.

I'm not going to try to put you off from complaining at all, but if you really want to be constructive about it, complain to the right places (and if you want to be really helpful, provide patches :)).  The rest of the developers and I are very open to ideas and additional help.

Additionally, the entire spirit of the project (as you've identified) is to make it a more Ubuntu like experience in that you have a lot of the little things handled for you.  Ideally someone shouldn't *have to* read the manual to get things to work. You ask why the backend is automatically started after you exit mythtv-setup?  Well that stems from multiple posts on a forum and confusion on IRC back in 2006.   You are the first person to complain about it.  Can you name a single circumstance that you *don't* want the backend running *after* you've configured it?

---

### Post by tgm4883 on 2008-01-25
> **the Goat said:**
> No I didn't over look that at all.  I am asking for the apt-get method to be officially supported in parallel to the mythbuntu method.  Right now in the official MythTV Gusty documentation it tells you to install mythbuntu ([link](https://help.ubuntu.com/community/MythTV_Gutsy)).  That is the only option presented to the user.  The core of my rant is that it is a mistake to present mythbuntu as the sole MythTV solution on Ubuntu.

The guide is for new users?  With a power user like yourself, why do you need a guide?

---

