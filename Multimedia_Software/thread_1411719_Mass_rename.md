---
title: "Mass rename"
date: 2010-02-20
forum: Multimedia Software
---

### Post by frt975 on 2010-02-20
I've downloaded the [following site]("http://ubuntuforums.org/www.classicalmidi.co.uk") using wget, and now I want to rename the midis by the text that links to them. eg. abc is a hyperlink to 431.mid. How do I change 431.mid to abc.mid

---

### Post by Barriehie on 2010-02-20
> **frt975 said:**
> I've downloaded the [following site]("http://ubuntuforums.org/www.classicalmidi.co.uk") using wget, and now I want to rename the midis by the text that links to them. eg. abc is a hyperlink to 431.mid. How do I change 431.mid to abc.mid

I'm not having any luck generating any kind of file to work with.  Perhaps post a bit of the file you want to process?

---

### Post by frt975 on 2010-02-20
I ran this command: ```
wget -rk http://www.classicalmidi.co.uk
``` to download the site.
Now I want something that will parse all the html pages and  erase everything but ```
_***<P><A HREF="music2/2571marci.zip">(2571)"Marcia in Sib maggiore"***_ a lovely piece. Donated & Sequenced by David.</A>This is a large file please<A href="pkunzip.exe"> click here. </a> for pkunzip.exe 
</b>
```and then rename```
 ./music2/2571marci.zip
``` to ```
Marcia in Sib maggiore.2571.zip
```

---

### Post by Barriehie on 2010-02-20
Okay, gawk can do that but I've got to go for a bit and can then post back.

---

### Post by Barriehie on 2010-02-20
Just noticed in the rename you can't have a '/' character as part of the file name because it's going to be part of the path construct.

---

### Post by Barriehie on 2010-02-21
file2hd.com can get the files.

---

### Post by Barriehie on 2010-02-21
I was just going through the manpage of wget and you can specify an accept/reject list of filenames to retrieve.  You'ld be able to dl just the .zip files with that option.

---

### Post by frt975 on 2010-02-22
Thanks for your effort, but I know how to download the files; they're sitting on my HD.
As for the "\" character I repaired my post.

---

