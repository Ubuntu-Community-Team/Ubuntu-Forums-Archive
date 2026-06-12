---
title: "lives &quot;you should install mplayer with pcm/wav support&quot;"
date: 2010-06-20
forum: Multimedia Software
---

### Post by bobdobbs on 2010-06-20
Hi all.

I'm setting up lives on lynx.


Upon the automatic testing of teh lives configuration, I get some test failures.
I am unsure how to resolve these.

The failures I get:

checking if sox can convert audio
Failed"you should install sox_fmt_all or similair

This one might be resolved. Using apt-cache, I found a package that matches this name

The remaining failures seem to be related to mplayer.
My system and all packages are up to date with what is in the repos. Is mplayer in the repos out of date?
Is it possible to upgrade mplayer to make lives fully functional ?

Checking if mplayer can decode to png/alpha
Failed
You should install mplayer with pcm/wav support

Checking if mplayer can convert audio
Failed
You may wish to upgrade to a newer version

Checking if mplayer to jpeg
Failed
You should install mplayer with either  png/alpha or jpeg support

---

### Post by mc4man on 2010-06-20
> Is mplayer in the repos out of date?
mplayer in ubuntu is always out of date and will continue to be so.

There are many ppa's that offer fresher and better configured mplayer and mencoder builds - here's one
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by no2498 on 2010-06-20
lives uses jack audio make sure pitivi does not uninstall it  

hope this helps

---

### Post by bobdobbs on 2010-06-21
> **mc4man said:**
> mplayer in ubuntu is always out of date and will continue to be so.

There are many ppa's that offer fresher and better configured mplayer and mencoder builds - here's one
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Thanks.

I've set up that repositry and used it to update mplayer.

However, I still get the same errors when starting up lives.

---

### Post by mc4man on 2010-06-21
> However, I still get the same errors when starting up lives. 
Have a self built mplayer here but to check went ahead and removed, installed the lucid mplayer .deb [from rvn ppa]("https://launchpad.net/~rvm/+archive/mplayer/+packages") and installed/ran lives - no problem - see screen.

Maybe try going into home folder and deleting the .lives file (hidden file

Where are you getting lives from - lucid repo or elsewhere?

---

### Post by bobdobbs on 2010-06-21
Alas, this process doesn't work for me.

I uninstalled mplayer, and installed mplayer from that ppa.

I then removed both the lives directories, and started over.

I'm still getting the same problem: the lives initation process insists that my version of mplayer has no pcm/wav support and cannot decode to png/alpha or jpeg.

I am getting lives from where-ever the default location is.

---

### Post by mc4man on 2010-06-21
A quick ck. shows that with the lucid repo mplayer lives will fail 3 tests, and replacing that mplayer with the ppa version will continue to fail the pcm/png test unless you do as previously suggested

> Maybe try going into home folder and deleting the .lives file (hidden file

If you don't see then Ctrl+h on keyboard

You must delete that **file** - when starting lives you'll start back at the orig. 'welcome to lives' screen and all will be well.

---

### Post by bobdobbs on 2010-06-21
> **mc4man said:**
> A quick ck. shows that with the lucid repo mplayer lives will fail 3 tests, and replacing that mplayer with the ppa version will continue to fail the pcm/png test unless you do as previously suggested

If you don't see then Ctrl+h on keyboard

You must delete that **file** - when starting lives you'll start back at the orig. 'welcome to lives' screen and all will be well.

Tested and failed.

I deleted .lives and .lives-dir.
Yet the mplayer tests are still failing.

---

### Post by bobdobbs on 2010-07-13
Bump.

Does anyone know how to get lives to pass the tests?

Failing that, are there other video editors that will run on ubuntu?

(I've tried kdenlive, but that also seems impossible to get working)

---

### Post by bobdobbs on 2010-08-17
bump

---

### Post by babarosa on 2011-02-19
Hi there,

my answer is a bit late, but I saw you are still around.

Using (X)Ubuntu 10.04.2 LTS, activate these and only these (for not to mix with versions from other repos) ppa's for

1) installing mplayer and mencoder
[https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=lucid](https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=lucid)

2) LIVES v1.4.0
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid/+index?field.series_filter=lucid&start=75&batch=75](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid/+index?field.series_filter=lucid&start=75&batch=75)

After installation, be sure to delete the hidden .lives file, before starting the new LIVES.

On my Xubuntu system, these packages installed just fine and now all the tests are passed!

Another alternative is "OpenShot" Movie Editor, looks very fine too.
[http://www.openshot.org/ppa/](http://www.openshot.org/ppa/)

Both guys from Lives and OpenShot deserve our deepest respect! =D>

For both editors, don't forget to install freir-plugins. For 3d animated effects in openshot, install blender.

Regrads,
Michael

---

### Post by bobdobbs on 2011-02-20
Hi Michael.
Thanks for jumping in.

Since I started the thread, I updated my distribution to Koala.
I hadn't started lives since I upgraded.

I just started lives now to see how it would load, and it was able to pass all the tests.

---

