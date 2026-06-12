---
title: "f-spot &quot;Send by Email&quot; to Evolution failure in Jaunty"
date: 2009-05-31
forum: Multimedia Software
---

### Post by joseelsegundo on 2009-05-31
I'm having some troubles in 9.04 with the process of using f-spot (via Photo->"Send By Email" in f-spot)  to generate an Evolution email with some pictures attached to the email.  This was working in 8.10.

Previously, when I clicked "Create Email" in the "Send By Email" dialog, the new email with the pictures would show up within a few seconds.  Now when I click "Create Mail" nothing happens for at least a minute, when finally Evolution throws up an error message saying it can't find the file in /tmp/blahblahblah.

I opened up a terminal window, and when I click "Create Mail" F-spot creates a directory in /tmp, and puts the resized photo for the email in there.  After a while, but before the Evolution error message pops up, the temp directory gets deleted.  I can't tell which process is the culprit in deleting the directory.

Obviously there are workarounds, however this is my wife's machine and she would greatly prefer to continue creating emails this way.  She's been a good sport so far with Ubuntu (it was a replacement for her ancient G3 Mac), so hopefully we can get this fixed for her.

Thanks

---

### Post by joseelsegundo on 2009-06-01
OK, Google search is my friend...

This is a known issue in f-spot.  See [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/77135](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/77135) for the description.

The answer is to increase the number of seconds that f-spot waits until it deletes the temporary image file.  To do this, you need to change the /apps/f-spot/export/email/delete_timeout_seconds key in your gconf.  There's a bit of a snag here as this key doesn't exist in the default install, so to add the key and set the value do this:

1. Open a terminal window
2. Run ```
gconf-editor
```
3. In the left-hand menu bar in the Configuration Editor open apps->f-spot->export->email
4. Left-click in the window in the upper right (where the auto-rotate and size keys are).
5. Select "New Key" from the popup menu
6. In the New Key form enter:
[INDENT]Name: delete_timeout_seconds
Type: Integer
Value: the number of seconds for the timeout (I use 300 seconds, which is 5 minutes)[/INDENT]
    
7. Click "OK"
8. Exit out of the Configuration Editor

Yay!  Mrs. Joseelsegundo is happy with f-spot once again! :)

---

