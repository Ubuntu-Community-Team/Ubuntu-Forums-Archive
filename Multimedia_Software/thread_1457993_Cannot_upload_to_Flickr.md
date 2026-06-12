---
title: "Cannot upload to Flickr"
date: 2010-04-19
forum: Multimedia Software
---

### Post by fedira on 2010-04-19
Hi all,

I posted this on Absolute Beginner Forum and received no replies. Thought someone here might be able to help. 

I'm trying to upload my friend's photos on her computer running 9.10 Karmic. I use JUploader on my old Ubuntu system, so that was the first thing I tried, but nothing happened when I clicked Upload. So then I tried FlickrUploader, KFlickr, and Desktop Flickr Organizer -- none worked at all, even for uploading a single photo. Either the "upload" function would be totally nonfunctional, or it would just hang without uploading a single photo. Similarly, the uploaders at flickr.com -- both the Uploadr and the basic uploader -- do not work at all, which is truly puzzling. We've tried this from multiple internet connections, while I've successfully uploaded photos using the very same connections. My friend reports she can't even attach a photo to an email.

I'm currently trying the flickr_uploader command-line option, but it just hangs -- no error message or anything.

Why could this be happening? Could it be a firewall issue? Uploading works fine from the same computer with the same internet connection when it's booted into Windows. I'm totally stumped, but I'd really like to get this figured out as my friend is a photographer and will not be able to use Ubuntu if she can find no way to upload her photos.

Thanks for any help!

---

### Post by Felix-the-Cat on 2010-04-20
That is very strange indeed. I would check the following if you haven't:
[LIST=1]
[*]File Permissions
[*]Firewall - "sudo iptables -F OUTPUT" (is Firestarted installed?)
[*]Check on the photo size, maybe they are too large
[*]Try using Fspot
[/LIST]

---

