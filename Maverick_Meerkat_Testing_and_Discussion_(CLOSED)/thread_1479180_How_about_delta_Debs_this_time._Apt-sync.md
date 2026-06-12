---
title: "How about delta Debs this time. Apt-sync?"
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Mutiny32 on 2010-05-10
This has been proposed and deferred for at least two or three releases and is a major bandwidth saver for users on slow or metered connections. The previous thread [here]("http://ubuntuforums.org/showthread.php?t=1460414")was locked from Lucid being released, so I thought I'd try to get it in here early, since popular changes that aren't implemented are usually blamed on no suggestion during a UDS. So Here. Before the first one. I'd like to see this implemented. We're wasting resources on small changes and creating big, bulky updates. Windows Update has been doing this for ages and it has been implemented for RPMs.

WHO'S COMING WITH ME, MAN!?

---

### Post by 23meg on 2010-05-10
> **Mutiny32 said:**
> since popular changes that aren't implemented are usually blamed on no suggestion during a UDS. So Here.

The way to "suggest" a feature for UDS discussion is to draft a [feature specification]("https://wiki.ubuntu.com/FeatureSpecifications"), propose it for discussion at UDS, be there yourself (in person or through remote participation) to make your case, get a group of people to work on it (or commit to working on it yourself) and get approval from the relevant people and/or teams. Forum threads are not of any real use, during UDS or not.

Fortunately for you, all of that has already been done, and there's already [an approved specification]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads") for this particular feature, so people who want to increase the likelihood of it being implemented in Maverick can contact the assignee and learn how they can help. There's not much else left to be done.

---

### Post by Speed_arg on 2010-05-10
YES PLEASE

I'm tired of downloading 400mb updates.

---

### Post by Mutiny32 on 2010-05-10
> **23meg said:**
> The way to "suggest" a feature for UDS discussion is to draft a [feature specification]("https://wiki.ubuntu.com/FeatureSpecifications"), propose it for discussion at UDS, be there yourself (in person or through remote participation) to make your case, get a group of people to work on it (or commit to working on it yourself) and get approval from the relevant people and/or teams. Forum threads are not of any real use, during UDS or not.

Fortunately for you, all of that has already been done, and there's already [an approved specification]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads") for this particular feature, so people who want to increase the likelihood of it being implemented in Maverick can contact the assignee and learn how they can help. There's not much else left to be done.

:) I know, I just wanted to cover all of the bases so it can't be claimed that this was never mentioned anywhere.

---

### Post by Starks on 2010-05-10
delta debs and apt-sync were approved for discussion at UDS this week.

[https://wiki.ubuntu.com/FoundationsTeam/Maverick/Planning/UDSBrussels](https://wiki.ubuntu.com/FoundationsTeam/Maverick/Planning/UDSBrussels)

---

### Post by xir_ on 2010-05-11
this is an interesting point. I wonder how much it costs canonical to send each Gb of updates?

There are a lot of improvements that can be done with the updater. Such as installing packages at the same time as downloading them to speed up the process and finding ways or reading the package database faster.

---

### Post by nanog on 2010-05-11
I wonder how many tons of CO2 emissions will be eliminated by delta-debs and apt-sync. We also badly need improved server suspend.

---

### Post by Mutiny32 on 2010-05-12
> **Starks said:**
> delta debs and apt-sync were approved for discussion at UDS this week.

[https://wiki.ubuntu.com/FoundationsTeam/Maverick/Planning/UDSBrussels](https://wiki.ubuntu.com/FoundationsTeam/Maverick/Planning/UDSBrussels)

Sweet. :guitar:

---

### Post by Mutiny32 on 2010-05-12
> **nanog said:**
> I wonder how many tons of CO2 emissions will be eliminated by delta-debs and apt-sync. We also badly need improved server suspend.

It would be great to know after it makes it into 10.10 and someone crunches the numbers on the amount of bandwidth saved and translates that into carbon emissions.

---

### Post by MadCow108 on 2010-05-13
I guess carbon emissions are going to rise due to delta debs as the clients need to do more cpu work = more power consumption.
I don't think there is much emission by transferring less over the network, the routing must be done anyway.

---

### Post by Slug71 on 2010-05-19
Looks like we might have to wait on this. 

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads)

Says approved but deferred.

---

### Post by zekopeko on 2010-05-19
> **Slug71 said:**
> Looks like we might have to wait on this. 

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads)

Says approved but deferred.

The definition of the spec is approved. The implementation is deferred but the last entry on the whiteboard is during Lucid development.

---

### Post by Penguin Guy on 2010-05-19
This has been mentioned many times before, the Ubuntu team are well aware of this but I guess they just have something against delta debs and apt-sync.

[LIST]
[*][Blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads")
[*][Brainstrom]("http://brainstorm.ubuntu.com/idea/13/")
[/LIST]

---

### Post by Slug71 on 2010-05-19
> **zekopeko said:**
> The definition of the spec is approved. The implementation is deferred but the last entry on the **whiteboard is during Lucid development**.

Yeh thats what makes me unsure.

---

### Post by Progressive on 2010-05-29
What would be the rationale for not implementing this? It looks like most of the technical issues have been worked out. 

If there is nobody interested in implementing this in the community, surely Canonical would want to put resources towards this, considering it would save them so much bandwidth, along with other benefits.

---

### Post by ranch hand on 2010-05-29
I am wondering how you implement this keeping in mind the folks on dial up connections.

This may not be a problem, I really don't know.

I do know that Ubuntu seems to be somewhat blind to those people and hope that this would not have any bad effect on them as does the difficulty in just connecting does.

---

### Post by ronacc on 2010-05-29
I don't think they are blind to them , they were the excuse they used for years to not go to a dvd for releases although they have done just that now .

---

### Post by ranch hand on 2010-05-29
> **ronacc said:**
> I don't think they are blind to them , they were the excuse they used for years to not go to a dvd for releases although they have done just that now .
I am not sure that is much of an excuse.  I never had a fast enough connection for a CD ISO download.  I ordered mine.

Ubuntu is though the hardest distro to get dial up to work on.  Just about all the rest are very easy (4 questions during installation and you are hooked up when you reboot to the OS).

So anytime that they change some thing that can adversely effect dial up users I worry.

---

### Post by ronacc on 2010-05-29
back around the start of dapper and before when I was stuck on dialup I had an external USrobotics and used WVdial to connect. the setup was easy ,of course some modems weren't supoorted , most real ones were, many of the fake (winmodems) weren't . for a cd d/l I just let the thing grind away all night anyone who wanted to call me after 10PM were out of luck :lolflag:

---

### Post by cariboo on 2010-05-29
Back when I was still on dial-up, you could buy Linux distro's in the local stationary/office supply store. I never downloaded an iso until I had high speed.

When I was on the Xandros beta test team, they sent out cds via courier, I always had a new cd 2 days after a new version was released. :)

---

### Post by ranch hand on 2010-05-29
> **ronacc said:**
> back around the start of dapper and before when I was stuck on dialup I had an external USrobotics and used WVdial to connect. the setup was easy ,of course some modems weren't supoorted , most real ones were, many of the fake (winmodems) weren't . for a cd d/l I just let the thing grind away all night anyone who wanted to call me after 10PM were out of luck :lolflag:
Yep, Hardy was the last release that dial up configuration was fairly easy.  As you say, a real modem is needed.

I think it is needed in any OS.

Mine, unfortunately, is an internal and that does make it more difficult.

Mandriva, and the other RPM based OSs are the easy ones and they don't mind an internal.

Of coarse then you have to deal with RPM and it is slower on dial up than DEBs by a long shot.

And it is not Ubuntu.  I like Ubuntu.

Dial up should  be easier though.

I like this basic concept but think that they are going to have to stick with the current set up, at least as an option, for it to work for folks on dial up.  I know that, for instance, that torrents just do not work there well, at least they did not for me (some of the distros I tried were respins and they like you to use torrents).  Ubuntu torrrents didn't even work an they are well seeded.

If you are on dial up I thing the buggers ignore you and you are too limited in speed anyway.

---

### Post by ranch hand on 2010-05-30
> **cariboo907 said:**
> Back when I was still on dial-up, you could buy Linux distro's in the local stationary/office supply store. I never downloaded an iso until I had high speed.

When I was on the Xandros beta test team, they sent out cds via courier, I always had a new cd 2 days after a new version was released. :)
I got all my CDs from LinuxCD.

The courier deal sound neat.  Quicker than dial up anyway.

The current sized CDs would take over 3 days at the top speeds I was able to get on dialup assuming no disconnects.  With interruptions it could well be over 4 days and I hate to think of running the md5sum after that and having to start over.

The ones I bought, I usually had in 4 days (mail delivery 3 times a week).  We were kind of remote.

---

### Post by ronacc on 2010-05-30
I just had the one external that I moved from box to box , I was cheap, one good external was cheaper than 3 0r 4 internals . Dapper was the first Ubuntu I used as a main system ,prior to that I was a Suse fan ( the novel / MS deal poisoned me on Suse ) so I know what you mean about RPM . I also use Sabayon which is gentoo based so I have to deal with portage too , talk about brain drain .
best we don't drift too far off topic or they'll black flag us .

---

### Post by VMC on 2010-05-30
I still have my old USB external modem. I will never forget the god-awful sound they made when trying to connect.

I remember when the fax part became the rage. Wow, I just had to have one. Very expensive by todays standards.

Hope I never have to here that sound again. Also "You got Mail" voice from AOL. How ancient that is.

Now I think of my DSL 768 is very slow. I'm thinking of going fiber.

---

### Post by Eddie Wilson on 2010-07-14
> **ranch hand said:**
> I am wondering how you implement this keeping in mind the folks on dial up connections.

This may not be a problem, I really don't know.

I do know that Ubuntu seems to be somewhat blind to those people and hope that this would not have any bad effect on them as does the difficulty in just connecting does.

How would this have a bad effect on persons with dial-up connections? Seems to me it would be better. I haven't been on dial-up for several years but I was just curious.

---

### Post by renkinjutsu on 2010-07-14
> **nanog said:**
> I wonder how many tons of CO2 emissions will be eliminated by delta-debs and apt-sync. We also badly need improved server suspend.

> **MadCow108 said:**
> I guess carbon emissions are going to rise due to delta debs as the clients need to do more cpu work = more power consumption.
I don't think there is much emission by transferring less over the network, the routing must be done anyway.

I remember reading something similar to this [here]("http://googletalk.blogspot.com/2008/03/google-talk-goes-green.html")

---

### Post by ranch hand on 2010-07-14
It is my impression, and I am good at being wrong, that some of this requires a little bit better speed than you get with dial up, at least the dial up around here.

It is like torrents.  Everyone seems to love them.  I do.  Do not try them on dial up.  Servers can't even see you.  Even boinc now wants you to have a 40Kb connection now.

On dialup I had 4.4Kb on a good day.

What worries me is that the system now works well with dial up.  Slow but good.  If you loose the connection it is handled well.  If any little thing does not work as well as it does now, though, getting update/upgrade could turn into a nightmare.

There are a lot of folks still on dial up and I really think we do need to think of them first.  A system that will work on a slow connection will work on a fast one.  This is not always true the other way around.

---

