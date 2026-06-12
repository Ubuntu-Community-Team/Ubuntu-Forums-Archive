---
title: "Can't connect to schools network drive"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by CodedOne on 2012-03-01
Howdy! I'm quite new to Linux and Ubuntu, so please bear with me if I am making an elementary mistake.

So I am trying to access some files that I have stored on my school's computer science server. At first, I tried using [this]("http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/") guide, but it did not work. I do believe I have gone through and reverted all of the changes that I have made.

So now all I'm trying to do is access it directly through the file system. I open the Home Folder, go to Network places, press ctrl-l and type in the name of the file system "network://filer.cs.tamu.edu/myusername". Usually when I do this on a windows computer, I need to put in my username and password in a dialogue box that opens up. In this case, no such dialogue opens. Instead, I get an error saying:

> Could not display "network://filer.cs.tamu.edu/myusername".

Error: DBus error
org.freedesktop.DBus.Error.InvalidArgs: Mountpoint
Already registered
Please select another viewer and try again.

Because the error is telling me "Mountpoint Already registered", I fear I may have messed something up when using that guide, but to be completely honest, I have no idea whats wrong.

Is there anything I can do to access my files?

Any help is greatly appreciated!

---

### Post by dandnsmith on 2012-03-02
> **CodedOne said:**
> Usually when I do this on a windows computer, I need to put in my username and password in a dialogue box that opens up. In this case, no such dialogue opens.

Therein lies a clue. I've seen people having problems with this sort of academic network in the past. The dialog box doesn't appear, and there appears to be no way to fake it.
If I'm right in my inferences, you'll have a problem as the networking people won't understand your problem, and will probably suggest you use Windows.
There may well now be a solution - but I'm neither aware of it, nor how to find it.
Talk to the people responsible for the network, and see if they can help.

---

