---
title: "How do I add auto display all available smb shares under Network in Nautilus?"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by EarlsFurniture on 2012-01-14
I have a mixed network with Ubuntu 10.04 x64 running as a server with samba shares so the XP machines on the network can see the file server.

I also have other *buntu boxes on the network. When using nautilus in one of these, I'd like all smb shares, both on the server, and any shared folders on the XP boxes to automatically show up under the Network heading in the bottom left pane.

Presently I have to click Entire Network > Windows Network > Main (my workgroup name) > the computer I want to connect to > the folder I want to browse.  After doing so, an entry under Network shows up that is "ejectable" or unmountable if needed.  It stays mounted till I unmount it.  But I don't want to go through all that trouble each time to mount every share.

I presently have these shares mounted in /mnt/smb/sharename via fstab at boot on the client machines in question, with bookmarks under Personal in nautilus, but I'd like to reduce clutter there especially since some of them are similar names to default user folders.  i.e. - there is a "documents," "pictures," "music," folders on the server so the user's bookmarks under Personal look like:

**Personal**
-User
-Desktop
-Downloads
-Documents
-Pictures
-Videos
-documents
-pictures
-music

**Devices**
-File System

**Network**
-Entire Network

I'd rather they show up as:

**Personal**
-User
-Desktop
-Documents
-Downloads
-Pictures
-Video

**Devices**
-File System

**Network**
-Entire Network
-Server
--documents
--music
--pictures

or

**Network**
-Entire Network
-documents on Server
-music on Server
-pictures on Server

The shares don't have to automount, but if I could make it that way for some it would be nice.

In short, I want to add bookmarks to the Network section, or better yet, show all computers and their shares automatically under the Network section without having to click though and mount each one individually every session. (or after unmounting)

Perhaps NFS might allow me to do this instead of Samba, I don't know.  But can I share the same folder via NFS for any *nix box on the network but still share them via Samba so the XP boxes can see them as well?  Could that create havoc with two network sharing types when two unique users try to access the same file? (in other words, since different network daemons control file access does one know what the other is doing?)

Or, is this simply a lacking feature in Nautilus that doesn't exist?

Are there other file managers that do work this way?

Also, if this isn't asking too much, I have some remote network connections that I'd like to show up in their own Category.  I use these for web server access on remote hosting services.  I guess this would be a custom bookmark category, or at least a category of any bookmarked remote-server connections. (created via "Connect to server..." under the Places menu.)

---

