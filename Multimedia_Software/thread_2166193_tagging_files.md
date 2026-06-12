---
title: "tagging files"
date: 2013-08-08
forum: Multimedia Software
---

### Post by akagashi-kama on 2013-08-08
Hello, I'm looking for a program to tag various types of files: documents, photos, music, video. Is there any program like that? All the better if it's Windows/Linux, so ?I could see/make tags on both of OS. 

Thanks

---

### Post by TheFu on 2013-08-08
> **akagashi-kama said:**
> Hello, I'm looking for a program to tag various types of files: documents, photos, music, video. Is there any program like that? All the better if it's Windows/Linux, so ?I could see/make tags on both of OS. 

Thanks

Do you mean a program that adds metadata to the headers for different file types?  Sorta like EXIF is for image files, but for any type of document?
I've worked professionally in document management. Metadata that is correct is fantastic, but in most environments, it is wrong, so it is worse than worthless.

Is there a specific program (any platform) that you are using today? I'm very interested in this problem space.

In my years doing this stuff, I've come to the realization that **a good search tool is the only real way to solve this problem.**  **Recoll** is amazing for indexing and searching on Linux - it is like having google for your personal machine - without having to share any information with anyone external. There is a nice GUI, but there is also a CLI that can be hooked up to a web server if you like. The trick is to have good metadata for your content that isn't text (images/video/audio), but just have good title, author, date, subject information for spreadsheets, wordprocessor, slide-desk docs, HTML files and others files.

Sadly, this means that other programs will be needed to properly set the metadata - id3 tags, EXIF information, etc ...  Storing metadata outside the source file will be impossible to maintain long-term. It requires more discipline than any human has.  I've seen commercial management systems for extremely exacting file types fail because people couldn't be made to follow the rules.

Does this make any sense?

Google found this: [http://askubuntu.com/questions/36357/any-programs-to-help-tag-organize-files](http://askubuntu.com/questions/36357/any-programs-to-help-tag-organize-files) - a few options provided.

Anyway - I don't have all the answers - love to hear how people address these issues.

---

### Post by akagashi-kama on 2013-08-09
Thank you for the info.

If I could make it exif-like it would be great, that would be what I was thinking about.

Lately I have made hundreds of GB of photos and videos. They're stored in chronological order, but sometimes I need to search them by people or place (not based on the GPS alone but things like "my university" etc.) or subject. I could use it to sort out some other files too.

I'm not using any specific program now. I'll try your suggestions, thanks.

---

### Post by TheFu on 2013-08-09
> **akagashi-kama said:**
> Thank you for the info.

If I could make it exif-like it would be great, that would be what I was thinking about.

Lately I have made hundreds of GB of photos and videos. They're stored in chronological order, but sometimes I need to search them by people or place (not based on the GPS alone but things like "my university" etc.) or subject. I could use it to sort out some other files too.

I'm not using any specific program now. I'll try your suggestions, thanks.

This [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) is all the info that I have. For photos, I've been using a hacked version of [http://fuzzymonkey.net/software/photogallery/](http://fuzzymonkey.net/software/photogallery/) for about a decade. My version just adds description and filename searching plus infinite directory levels.  It has been years since I modified the code.  I provided the patches back to the author years ago, but he wasn't interested. I should put them into git.  It isn't a very pretty webapp, but someone with design skills can make it pretty.

---

