---
title: "Save Options, File &gt; Save As... &gt; Why Not To Network?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by sjl127 on 2009-01-25
Is there a way to go to File > Save As... > and choose a network drive?  

Or can I only save to my local disk?

Thank you.

---

### Post by wylfing on 2009-01-25
Saving across the network works fine. I am guessing here, but I suspect you are trying to save to a Windows share, and your frustration is that the share doesn't show up in the Save As dialog box (and Network isn't there either).

Try adding a bookmark for your Windows share.
[LIST=1]
[*]Choose Places > Connect to Server from the main menu bar.
[*]Change Service type to Windows share.
[*]Enter appropriate information in the Server, Share, and User Name boxes. You can leave the others blank.
[*]Enable the Add Bookmark checkbox and supply a suitable bookmark name. The bookmark name is whatever you want to show up in the bookmarks list...for example, "Public files" or something similar.
[*]Click Connect.
[*]Provide the name of your workgroup and your password for the Windows share you are accessing.
[/LIST]

Now when you choose Save As from your application, you will see your bookmark in the left-hand panel. Just click on that.

EDIT: I seem to recall being able to press Ctrl+L in a Save As dialog and type paths directly. I wonder why this functionality disappeared. It was useful.

---

