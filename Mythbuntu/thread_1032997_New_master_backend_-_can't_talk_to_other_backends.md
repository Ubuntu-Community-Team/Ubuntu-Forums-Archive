---
title: "New master backend - can't talk to other backends"
date: 2009-01-06
forum: Mythbuntu
---

### Post by stdPikachu on 2009-01-06
Gak!

Having just moved house and finally been allowed some holiday I decided to rejog my ailing Gentoo master backend with a new Kubuntu-based one (8.04) - that all went hunky dory, by the way, and the new backend appears to work fine (old database was re-imported and important settings changed)

However, if I try and play back a TV show recorded on banquo (slave backend) on prospero (master backend), the player exits out and I get the following messages in the master mythbackend.log;
```
2009-01-07 03:22:09.022 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-01-07 03:22:09.030 RingBuf() Error: Invalid file descriptor in 'safe_read()'
2009-01-07 03:22:11.667 MainServer::HandleAnnounce Playback
2009-01-07 03:22:11.667 adding: prospero as a client (events: 0)
2009-01-07 03:22:11.668 MainServer::HandleAnnounce FileTransfer
2009-01-07 03:22:11.668 adding: prospero as a remote file transfer
2009-01-07 03:22:11.670 ERROR: LocalFilePath unable to find local path for '1009_20090107001300.mpg', found 'myth://127.0.0.1:6543/1009_20090107001300.mpg' instead.
2009-01-07 03:22:11.676 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-01-07 03:22:11.678 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-01-07 03:22:11.678 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-01-07 03:22:11.687 RingBuf() Error: Invalid file descriptor in 'safe_read()'
2009-01-07 03:22:13.008 MainServer::HandleAnnounce Playback
2009-01-07 03:22:13.008 adding: prospero as a client (events: 0)
2009-01-07 03:22:13.009 MainServer::HandleAnnounce FileTransfer
2009-01-07 03:22:13.009 adding: prospero as a remote file transfer
2009-01-07 03:22:13.015 ERROR: LocalFilePath unable to find local path for '1009_20090107001300.mpg', found 'myth://127.0.0.1:6543/1009_20090107001300.mpg' instead.
2009-01-07 03:22:13.030 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-01-07 03:22:13.030 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-01-07 03:22:13.030 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-01-07 03:22:13.033 RingBuf() Error: Invalid file descriptor in 'safe_read()'
2009-01-07 03:22:16.008 MainServer::HandleAnnounce Playback
2009-01-07 03:22:16.008 adding: prospero as a client (events: 0)
2009-01-07 03:22:16.009 MainServer::HandleAnnounce FileTransfer
2009-01-07 03:22:16.009 adding: prospero as a remote file transfer
2009-01-07 03:22:16.012 ERROR: LocalFilePath unable to find local path for '1009_20090107001300.mpg', found 'myth://127.0.0.1:6543/1009_20090107001300.mpg' instead.
2009-01-07 03:22:16.030 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-01-07 03:22:16.030 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
```
Conversely, whenever I try and play back a file from prospero (master backend) on banquo I get another, slightly different error;
```
2009-01-07 03:25:36.747 Connecting to backend server: 192.168.1.30:6543 (try 1 of 5)
2009-01-07 03:25:36.747 Using protocol version 40
2009-01-07 03:25:40.935 AFD: Opened codec 0x83306e0, id(MPEG2VIDEO) type(Video)
2009-01-07 03:25:40.935 AFD: codec MP3 has 2 channels
2009-01-07 03:25:40.935 AFD: Opened codec 0x8d875e0, id(MP3) type(Audio)
2009-01-07 03:25:40.948 AFD: Opened codec 0x8d87960, id(DVB_SUBTITLE) type(Subtitle)
2009-01-07 03:25:40.948 AFD: codec MP3 has 0 channels
2009-01-07 03:25:40.948 AFD: Opened codec 0x8d87ce0, id(MP3) type(Audio)
2009-01-07 03:25:41.394 AFD: Opened codec 0x83306e0, id(MPEG2VIDEO) type(Video)
2009-01-07 03:25:41.395 AFD: codec MP3 has 2 channels
2009-01-07 03:25:41.395 AFD: Opened codec 0x8d72360, id(MP3) type(Audio)
2009-01-07 03:25:41.395 AFD: Opened codec 0x8d7d9e0, id(DVB_SUBTITLE) type(Subtitle)
2009-01-07 03:25:41.395 AFD: codec MP3 has 0 channels
2009-01-07 03:25:41.395 AFD: Opened codec 0x8d7dd60, id(MP3) type(Audio)
2009-01-07 03:25:41.817 [mpeg2video @ 0xb735aa88]ac-tex damaged at 14 21
2009-01-07 03:25:41.817 [mpeg2video @ 0xb735aa88]Warning MVs not available
2009-01-07 03:25:41.852 Error: File '/storage/tvstore/1022_20051130202800_20051130210000.nuv' missing.
2009-01-07 03:25:41.883 Error: File '/storage/tvstore/1022_20051130202800_20051130210000.nuv' missing.
2009-01-07 03:25:41.915 Error: File '/storage/tvstore/1022_20051130202800_20051130210000.nuv' missing.
2009-01-07 03:25:41.947 Error: File '/storage/tvstore/1022_20051130202800_20051130210000.nuv' missing.
2009-01-07 03:25:41.983 Error: File '/storage/tvstore/1022_20051130202800_20051130210000.nuv' missing.
2009-01-07 03:25:42.020 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.020 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.047 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.079 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.115 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.147 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.179 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.211 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.247 Error: File '/storage/tvstore/1510_20060919225800.mpg' missing.
2009-01-07 03:25:42.262 Error: File '/storage/tvstore/1536_20060830125800.mpg' missing.
2009-01-07 03:25:42.279 Error: File '/storage/tvstore/1536_20060830125800.mpg' missing.
2009-01-07 03:25:42.311 Error: File '/storage/tvstore/1536_20060830125800.mpg' missing.
2009-01-07 03:25:42.343 Error: File '/storage/tvstore/1536_20060830125800.mpg' missing.
```

From my limited knowledge of myth's labyrinthine internals, it looks like the master backend is trying to open a myth:// connection to the local backend (as evidenced by 127.0.0.1 - I'd expect something more like myth://192.168.1.20)... where the files aren't. And the slave backend is trying to open a direct file connection to the local /storage/tvstore (both backends use this path for local storage)... where the files aren't, since they live on /storage/tvstore on the master backend. I've been poking through the database and configuration options but can't really find anywhere I explicitly seem to be going wrong - although these new-fangled "storage groups" do worry me somewhat (and the docs don't really touch on it much). In any case, I set up a default and livetv storage groups on both backends, both pointing at /storage/tvstore and /storage/tvstore/.livetv respectively.

Can anyone give me any pointers on what to look for? I'm a bit FUBAR at the moment since only the slave backend currently has an aerial plugged into it, and I'm dependent on it for all my recordigs at the moment, and not having them available throughout is a pain.

Thanks in advance!

---

### Post by stdPikachu on 2009-01-06
OK, one problem solved - the BackendServerIP setting in the mythconverg.settings table was set to 127.0.0.1 instead of 192.168.1.20, which is banquo's network address. Changing this allowed prospero to pick up recordings from banquo, so that's the biggest problem solved, as abviously the prospero frontend was doing a DB lookup for banquo and being pointed to localhost instead of the network.

Anyone have any idea why the setup program would only log 127.0.0.1...? Unless I blithely ignored the option in mythsetup... :~S

---

### Post by stdPikachu on 2009-01-08
Fixed the other issue now.

For some reason, gentoo had been telling myth that the system hostname was actually the FQDN - as such, all my recordings had an invalid hostname entry. Running this bit of SQL on the recorded table fixed the issue with banquo not being able to play anything back (as it was looking for a backend called prospero.snafu.local rather than just prospero).

```
update recorded set recorded.hostname="prospero" where recorded.hostname="prospero.snafu.local";
```

---

### Post by SteveGodfrey on 2009-01-16
I have the same problem after upgrading the backend. I am a little stuck trying to run the sql script

update recorded set recorded.hostname="M" where recorded.hostname="M2";

I assume this needs to be run from with mysqladmin somehow. Can you point me in the right direction?

Thanks

---

### Post by SteveGodfrey on 2009-01-16
Got it.

mysql -u root mythconverg


mysql> update recorded set recorded.hostname="172.16.0.10" where recorded.hostname="m";
Query OK, 94 rows affected (0.01 sec)
Rows matched: 94  Changed: 94  Warnings: 0

---

