---
title: "Cannot open &quot;JPG&quot; files, security risk?"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by arron on 2007-02-11
I got a weird problem.  I cannot open a picture with a capital ".JPG" extension.  If i rename the file ".jpg" it opens no problem.  With a capital i get this error message:

[http://arron.dnip.net:81/files/Screenshot.png](http://arron.dnip.net:81/files/Screenshot.png)

How can i set ubuntu to open a ".JPG" file by simply double clicking it like i do with ".jpg"?  I assume it will do the same with gif or others capital extensions.  Is this a security risk or something?  It even does the preview icon for it as you can see in the screen shot.

Thanks

---

### Post by RRS on 2007-02-11
Possible Explanation?

Linux will choose an application to open a file with according to the contents of the file rather then the extension if you don't give specific instructions. That's why you can usually click on a file and have it open properly even if there's no extension in the file name.

I've occasionally gotten the same message when the contents of the file and the extension seemed to be in conflict or if the extension is simply misspelled, etc.

I'm guessing the security risk comes from the fact that the file may have been misslabled intentionally which seems to be an easy way to install malicious code thru e-mail attachments, etc. hence the reference to a tusted source.

I've never had a problem with changing the extension or selecting a different app to open the file with.

Of course I could be totally wrong. If so maybe someone can correct me. :)

---

### Post by tbroderick on 2007-02-11
You should rename the file to it's proper extension. Here's a very easy way to rename just the extension from .JPG to .jpg;

Open a terminal and change to the folder where your .JPG's are and paste this;
```
for i in $(find . -name '*.JPG'); do mv $i ${i//.JPG/.jpg} done

```

---

### Post by arron on 2007-02-14
Rename sounds easy, but i have lots of pics stored on CD's.  On a fresh install or ubuntu they opened without this error, and now they don't.  I tried a couple different apps to view with, but the biggest thing i did was put the xubuntu desktop package on, and i *think* this started happening soon after.

How or where can i tell it that a ".JPG" is ok or safe to open?

---

### Post by arron on 2007-02-25
bump.

Can anyone help out with this?  Im still haven this problem.

---

### Post by verzeletti on 2008-04-02
edit the file:

    **    ~/.local/share/mime/globs  **

remove or comment the line:

       ** application/x-extension-jpg:*.jpg**


This simple solution solved the problem here, without restarting the "X Server".

Ps.: I have been using the Ubuntu 7.10.

---

