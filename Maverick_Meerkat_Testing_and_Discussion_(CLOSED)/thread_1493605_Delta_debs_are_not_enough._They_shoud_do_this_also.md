---
title: "Delta debs are not enough. They shoud do this also."
date: 2010-05-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Speed_arg on 2010-05-26
Ok, delta debs might be great for updating, but when downloading a new package, we need a compression.

In Windows, when you download a program generally it is in a rar. We should make the repositories to send the package compressed and then decompress it for then installing it.

---

### Post by Longinus00 on 2010-05-26
> **Speed_arg said:**
> Ok, delta debs might be great for updating, but when downloading a new package, we need a compression.

In Windows, when you download a program generally it is in a rar. We should make the repositories to send the package compressed and then decompress it for then installing it.

Debs are compressed.

---

### Post by Seren on 2010-05-26
[http://en.wikipedia.org/wiki/Deb_(file_format](http://en.wikipedia.org/wiki/Deb_(file_format))

> 
Debian packages are standard Unix ar archives that include two **gzipped**, **bzipped** or **lzmaed** tar archives: one that holds the control information and another that contains the data.


---

### Post by 23meg on 2010-05-26
[https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma](https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma)

---

### Post by MacUntu on 2010-05-26
> **23meg said:**
> [https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma](https://blueprints.launchpad.net/ubuntu/+spec/dpkg-lzma)
That's only about the Packages files and the CD content - not the whole archive (not to mention that it seems abandoned).

---

### Post by 23meg on 2010-05-26
> **MacUntu said:**
> That's only about the Packages files and the CD content - not the whole archive

It was meant primarily to save space on the CDs, but applies to the whole archive.

> This change is being proposed primarily to save space on the CDs. It would also save bandwidth for downloads from Ubuntu servers. 

> Launchpad will need to be modified to support lzma uploads and to check that the needed predepends listed in the package.

[QUOTE=MacUntu](not to mention that it seems abandoned)[/QUOTE]

I linked to it for informational purposes; not sure about the status of deployment, despite the "Implementation" field listing "Deployment".

---

### Post by Speed_arg on 2010-05-26
Well, looks abandoned. Thanks.

---

### Post by cariboo on 2010-05-26
If you open a .deb file with the archive manager, you will see that they are compressed.

---

### Post by seeker5528 on 2010-05-26
> **MacUntu said:**
> That's only about the Packages files and the CD content - not the whole archive (not to mention that it seems abandoned).

If you read the full spec they do give figures about how much would be saved in the archive. Don't know if those are real figures or projections.

> **23meg said:**
> It was meant primarily to save space on the CDs, but applies to the whole archive.

Only the DVD and Alternate CD include .deb files, correct?

Later, Seeker

---

### Post by MacUntu on 2010-05-27
> **seeker5528 said:**
> If you read the full spec
Oops, missed that link. :oops:

---

