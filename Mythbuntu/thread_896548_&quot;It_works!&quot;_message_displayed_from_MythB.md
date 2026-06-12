---
title: "&quot;It works!&quot; message displayed from MythBuntu server"
date: 2008-08-21
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-21
If your mythbuntu server is located at [http://localhost](http://localhost), and you type in [http://localhost](http://localhost)  looking for mythweb, you may be greeted with a mostly blank web page stating "It works!".  Well, thanks but ***WHAT*** works?

Apparently, this means the apache2 server is up and running and displaying the contents of the file /var/www/index.html.  For example, if you replace the file /var/www/index.html with this paragraph, the notification might be more meaningful:

```
<html><body><h3>The Apache2 html server is running! </h3><h3>To access mythweb, try http://localhost/mythweb/mythweb.php</h3></body></html>
```

After this change, if you try to access your myth pc mythbuntu's server from another PC on your LAN using something like [http://192.168.1.106](http://192.168.1.106)  you'll be greeted with
> The apache2 html server is running!
To access mythweb, try [http://192.168.1.106/mythweb/mythweb.php](http://192.168.1.106/mythweb/mythweb.php)
My myth installation appears on my local area network (LAN) at ip address 192.168.1.106. Your installation probably has a different ip number than 192.168.1.106 so change the paragraph's ip numbers to your mythbuntu mythtv's local ip.

---

### Post by superm1 on 2008-08-21
So that file is coming from the default apache install.  I agree that we should try to modify it if possible.

Can you file a bug on mythweb so that this can be tracked?

---

### Post by LarryJ2 on 2008-08-21
Yes, the "unhelpful" ***It Works*** message is coming from the apache2 server as it dumps out the file **/var/www/index.html**  I guess I can ask for a change.  It isn't really a "bug" as what was coded is exactly what is happening.  I'll make an attempt anyway.

OK, I was able to file it as question:
> 
Open Open Question #42795, asked 2 seconds ago by LarryJ
Request to change /var/www/mythweb/index.html

At least two of us think that the default /var/www/mythweb/index.html could be changed to be more helpful.

I wonder if index.html could be changed in future editions of mythbuntu to something like the suggestion contained in the discussion found here:

[http://ubuntuforums.org/showthread.php?p=5636100#post5636100](http://ubuntuforums.org/showthread.php?p=5636100#post5636100)

Larry

---

### Post by mrand on 2008-08-21
> **LarryJ2 said:**
> Yes, the "unhelpful" ***It Works*** message is coming from the apache2 server as it dumps out the file **/var/www/index.html**  I guess I can ask for a change.  It isn't really a "bug" as what was coded is exactly what is happening.  I'll make an attempt anyway.

OK, I was able to file it as question:
There is a wishlist category in the bug section - I've moved your question there and added a few suggestions of my own.

Thanks for reminding the Mythbuntu team of this easily overlooked item!

[INDENT]Marc[/INDENT]

---

### Post by nickrout on 2008-08-21
How is this a bug? mythweb is always under the mythweb directory.

---

### Post by LarryJ2 on 2008-08-21
It's not really a bug in my mind. In the end, this became a "feature" request.

---

### Post by superm1 on 2009-03-30
For those following along, this will be available in the latest -fixes packages next Friday for hardy, intrepid, and jaunty.

It will be available tomorrow in the Jaunty standard mythtv updates.

See [https://bugs.edge.launchpad.net/mythbuntu/+bug/260126](https://bugs.edge.launchpad.net/mythbuntu/+bug/260126) for more information.

---

