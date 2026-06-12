---
title: "Install tvheadend"
date: 2017-03-19
forum: Multimedia Software
---

### Post by kadaitcha on 2017-03-19
Would someone who has actually installed tvheadend recently please advise me exactly how to install tvheadend, including every step necessary ? I've looked high and low without finding any straightforward instructions which work. It appears that the name of the file / repository / keys / whatever have been changed and the current details are the world's best kept secret.

Logically I'd expect 'sudo apt-get install tvheadend' to do the job however it appears there are unpublished gotchas one is expected to know and without knowledge of which there is no way to install tvheadend

Despite innumerable attempts, I cannot get around the 'Unable to locate package tvheadend' Surely this must be available somewhere.

I've tried to register on the tvheadend forum but it appears the conformation emails are not getting sent

---

### Post by ajgreeny on 2017-03-19
I have no idea which version of Ubuntu you are using but if it is 16.04 there is a ppa for tvheadend at [https://launchpad.net/~jonasped/+archive/ubuntu/ppa](https://launchpad.net/~jonasped/+archive/ubuntu/ppa)

Follow the instructions for adding that to your software sources and you should then be able to install the application in the usual way.

---

### Post by kadaitcha on 2017-03-19
Thanks, I'll try that. Why is it necessary for the runaround with tvheadend anyway ? Most ubuntu applications install in a straightforward manner but tvheadend is something else again.

---

### Post by ajgreeny on 2017-03-19
I can not help you with that query as I have never used tvheadend, and in fact, I do not really know anything about it.

However, have you seen and tried out all the possible ways shown at [https://tvheadend.org/projects/tvheadend/wiki/AptRepository](https://tvheadend.org/projects/tvheadend/wiki/AptRepository)

---

### Post by kadaitcha on 2017-03-19
Seems that repository actually works, thanks again to the much appreciated advice from ajgreeny. I'd  still like to know why tvheadend developers make it so ridiculously  difficult to find downloads. One would think from the difficulty I've  encountered and the key arrangement applicable to many repositories that  tvheadend is the greatest secret ever conceived. Reviews are  generally fairly complimentary to tvheadend, consequently one would  reasonably expect the developers want people to use it. Mind you it  doesn't appear to be possible to register for the tvheadend forum as the  confirmation emails don't exist.  Documentation appears hopelessly sparse with more points omitted than are included. For example, the configuration instructions assume things always happen in a certain way and do not even hint at what needs to be done when plans don't go smoothly which is more often than not in IT. Quite likely tvheadend is a very good thing but it could certainly do with far better documentation. That link is a good example in that most of the information is years out of date. Hopefully I'll be able to find some independent tutorials which include all the minor but critical points the official documentation neglects to mention,  [https://tvheadend.org/projects/tvhea.../AptRepository  ]("https://tvheadend.org/projects/tvheadend/wiki/AptRepository")

---

### Post by walterav on 2017-03-19
This official repo worked for me when I tried it a month ago, was it this key server thing?

```

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
echo "deb https://dl.bintray.com/tvheadend/deb xenial stable" | sudo tee -a /etc/apt/sources.list #NOTICE THE WORDS "XENIAL" & "STABLE"???
sudo apt-get update
sudo apt-get install tvheadend #set admin username/password

```

For more info
[https://ubuntuforums.org/showthread.php?t=2336566&p=13542231#post13542231](https://ubuntuforums.org/showthread.php?t=2336566&p=13542231#post13542231)

BTW which ubuntu version/architecture are you running i686 amd64?

---

### Post by kadaitcha on 2017-03-19
The keyserver thing is / was only part of the problem.  Is tvheadend subject to CIA / KGB control or something comparable ? Until ajgreeny was kind enough to give me the location of a current repository, I had no idea where to find the thing as either the keys or the repository were incorrect / outdated.  I'm using 16.04 because I'm re-installing over an old version of Kodi that came with a device I inherited. The system had far too many weird features to make it worth debugging, including its refusal to install TV tuners / backend. Mind you after the hair-tearing out experience I'm finding with tvheadend, I'm seriously considering ditching Kodi / tvheadend and trying an alternative solution like MythTV / Mythbuntu.  At least it appears that Myth has some semblance of official support whereas official tvheadend support is virtually non-existent.

---

### Post by walterav on 2017-03-21
> The keyserver thing is / was only part of the problem.

What was the other part of the problem with the default instructions?
[https://tvheadend.org/projects/tvheadend/wiki/AptRepository](https://tvheadend.org/projects/tvheadend/wiki/AptRepository)

If you would like to try the native tvheadend repository instead of using the unofficial ppa, please post the output of the following command if the instructions fail on you again.
```

cat /etc/apt/sources.list | grep tvheadend

```

---

