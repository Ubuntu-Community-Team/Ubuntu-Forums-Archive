---
title: "Downloading/converting Website trees? aka web books?"
date: 2008-09-11
forum: Multimedia Software
---

### Post by Stochastic on 2008-09-11
Hi, so I've got myself a fancy new sony e-paper reader and I'd like to start loading it up with good readings.  Essentially I want to figure out a way to take a website like this: [http://ccrma.stanford.edu/~jos/pasp/](http://ccrma.stanford.edu/~jos/pasp/) or this: [http://vagueterrain.net/journal10](http://vagueterrain.net/journal10) and take all the individual pages into a single readable file for my reader.  

Is there any automated script out there to do such a thing?  Do I have to manually save each page, strip them down to text form, then concatenate each page/article/chapter etc...?

The reader can handle html, pdf, txt, and lrf files (there may be others), so I know this can be done, but I'm wondering what the easiest way would be (that first link would take a LOT of time to do section-by-section).

---

### Post by leg on 2008-09-11
The scrapbook plugin for firefox would allow you to do that and you would have all the links altered to work on your filesystem. Wget will also do it and again alter links for your local file system. Have a look at the two and see which one you prefer.

---

### Post by Stochastic on 2008-09-11
I didn't realize wget would work on trees, what options do you need to invoke to do that?

The scrapbook plugin works fine, but it only copies all the files to my harddrive.  I want the entire 'book' in one file, so the simplest method I've found is to use html2lrf to convert the frontpage (with the link-level structure enabled).  Currently this method produces a result, but the link-level structure in html2lrf isn't smart enough to realize it already followed certain links and I'm getting repeated sections (not to mention some really wonky conversion formatting).  I'm going to keep playing with these tools and see how refined I can get things.

---

### Post by leg on 2008-09-11
```
wget -R http://ccrma.stanford.edu/~jos/pasp/
```should get you close. If not take a look at the [wget man page]("http://linux.die.net/man/1/wget") for more options. Also once you have it with bookmarks plugin you can do what you want with it so you could possibly convert it into one page.

---

### Post by lovinglinux on 2008-09-11
You could try [UnMHT]("https://addons.mozilla.org/en-US/firefox/addon/8051") extension for Firefox. It can save and view mht files (IE archive)  inside Firefox. 

I already tested it and works flawlessly. It saves an entire page as a single mht file. The only problem is that you can't save an entire web site, but maybe you could create your own index that points to each mht file.

Check if the e-paper supports mht.

---

