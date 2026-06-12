---
title: "Digital Radio via MythTV"
date: 2010-05-30
forum: Mythbuntu
---

### Post by chipppy on 2010-05-30
Good Morning

Does anyone know if/how Digital Radio can be received/setup through MythTV (Mythbuntu 10.04)

I can vaguely remember a MythFM plugin from a long time ago but that was analogue and has since stopped development from my web searches

I have run a few different web searches and cannot find anything that resembles even a plugin to receive digital radio.  Capabilities to record would be great.

I currently use a webcast outside of MythTV but would prefer to use an inbuilt feature so as to be able to use the full distribution capabilities of the MythTv server system to have radio via my MAME=box in the shed.  (Yes its sad but I am an old schooler at heart).

Silly thought but if nothing exists would anyone be willing to write something.  I am self learning programming (C#)at the moment so happy to help out (not much help as I am a noob at programming, but hey good learning opportunity)

Cheers
Chipppy

---

### Post by ian dobson on 2010-05-30
Hi,

MythTV doesn't support radio, but as long as you have a program that can tune to the required frequency (ivtvtune for PVR150/PVR500) and dump the audio to another process you could get it played back.

I wrote this perl script some time ago to "beam" an radio channel over my network to another box.

```

# Variables to be defined/configured
# LocalPort = Port number that this server listens on
# RemotePort = Port number to beam the info to
# IVTVDevice = Radio device to use
#
#
use IO::Socket;
my $LocalPort=27001;
my $RemotePort=27002;
my $IVTVDevice="/dev/radio0";
my $Frequency="";
while (1) {                                                     #Do forever
   my $sock = new IO::Socket::INET(
                                 LocalPort => $LocalPort,
                                 Proto => 'tcp',
                                 Listen => 1);                  #Open Port for listen
   my $new_sock = $sock->accept();                              #Wait for connection
   my $ClientIP = $new_sock->peerhost();                        #Save client IP address
   while(<$new_sock>) {
      $Frequency = $_;                                          #Get frequency
      $Frequency =~ s/\n//;                                     #Clean it up abit
   }
   print "Connection from $ClientIP $Frequency MHz\n";          #Abit of debug
   sleep 5;                                                     #Get nc on the client abit of time to startup
   system "ivtv-radio  -f $Frequency -d $IVTVDevice -c \"sox -t raw -r 48000 -w -s -c2 %s -t ogg - |nc  $ClientIP $RemotePort\"" 
}

```

On the otherbox I just used netcat to send the frequency to the server, then wait abit then run netcat that feds into sox to playback the audio.

EDIT: Also have a look here: [http://forums.sonos.com/archive/index.php?t-2580.html](http://forums.sonos.com/archive/index.php?t-2580.html) this sounds alot like my solution.

Regards
Ian Dobson

---

