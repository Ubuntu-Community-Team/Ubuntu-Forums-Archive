---
title: "Package to play Mp3,Mpeg,files"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by logintomyworld on 2007-10-06
Hello All


i have installed Ubuntu my pc i don't have the internet connection in my home, so can any one provide me the link to download the package , so that i have download the package from any browsing center and plug it to my system.......:):):)

---

### Post by RomeReactor on 2007-10-06
Hi. Open Synaptic (System->Administration->Synaptic Package Manager) and search for **gstreamer0.10-ffmpeg** and mark it for installation, then search for **gstreamer0.10-plugins-ugly** and also mark it for installation, then--still in Synaptic--go to "File->Generate package download script". This will make a script which you can then open in Gedit (or Nano, or whichever text editor you prefer) and in it you will see which packages you need to download along with gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly; namely, their dependencies. That list of packages is what you need to download, so you can open that script in NotePad in windows (or copy the packages mentioned in the file to a .txt; just don't mind the parts where it says "wget -c": that's a command line downloading program in Ubuntu. Just copy the lines beginning with "http" and ending in".deb". Those are the URLs of the packages you need to download.

Once you have them in your Ubuntu system (whether in a CD or USB device), open Synaptic again and go to "File->Add downloaded packages", navigate to where they are, and Synaptic will proceed with the installation.

Hope this helps. Post back if you have any doubts.

---

