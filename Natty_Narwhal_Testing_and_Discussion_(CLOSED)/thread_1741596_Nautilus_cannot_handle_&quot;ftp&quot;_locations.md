---
title: "Nautilus cannot handle &quot;ftp&quot; locations"
date: 2011-04-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Calash on 2011-04-28
I just loaded a fresh install of 11.04 on a new drive.  Did the basic updates and then went about moving over key files from my old 10.10 image.  Both builds are x64.

On the 10.10 I was able to setup bookmarks to my webserver FTP site.  These worked without a problem.  However the same bookmarks on my 11.04 give me the following error.

"Nautilus cannot handle "FTP locations"

Google gives a few hits as bug reports that were fixed several versions ago, but nothing of real value yet for this version.

Trying to go directly to the FTP site in the Location menu generates the same error.  Firefox is able to get to the FTP index and login without a problem.

Any ideas of how I can get this fixed up?

---

### Post by Calash on 2011-04-28
Never mind, I got the answer.

Using gvfs-mount in the command line got me an error about HTTP proxy not accepting the request.  This got me to the solution:

My computer is behind a proxy server.  When I was first setting everything up with 11.04 I was having various issues with Update Manager and manually put in the proxy info, forgetting that FTP needed a different port.  I filled out the correct Proxy info for my location and it is now mounting fine.

Hopefully Update manager is still working, but that is a separate thread.

---

