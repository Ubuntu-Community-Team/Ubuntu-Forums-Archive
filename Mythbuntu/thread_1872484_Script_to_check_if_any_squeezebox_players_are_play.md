---
title: "Script to check if any squeezebox players are playing before sleep"
date: 2011-10-30
forum: Mythbuntu
---

### Post by kaq on 2011-10-30
Hi

I somewhat a noob to linux. I am running a mythbuntu 11.04 combined front and backend with the latest stable squeezebox server 7.6 which is working fine :) but I want it to sleep when not use. For this I can use the guide here [http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup") however I don't want it to  shut down when a player is playing music through the SBS. I read the script sample /usr/bin/checklogin.sh on the mythttv wiki and I found  a script to check if SBS has any "active players" here [http://www.thespicers.net/squeezebox-stuff]("http://www.thespicers.net/squeezebox-stuff") (shutdown.pl). I get the big lines in what it is doing and know it is 2 different languages however I dont know how to translate or combine these 2 scripts :( I don't need the fancy warning system only the check for active players.

Thanks in advance
Kasper

---

### Post by ian dobson on 2011-10-31
Hi,

Why not just get the myth script to call the squeezbox script, where the squeezbox script returns 1 or 0, which the mythscript uses to decide if it should shutdown or not, maybe something like:-

SQUEEZ=´shutdown.pl´
if [ "$SQUEEZ" == "1"];then
 do shutdown stuff
endif

Regards
Ian Dobson

---

### Post by kaq on 2011-10-31
thanks now the sh script is working :) but something doesn't work in my modified perl script

modifications back
# to me so they can be included in future versions.
# If you use this script, please let me know!

# Shuts down the server if there aren't any players currently playing.
# Designed to be cronned every x minutes during a time range when the server
# should be off.
#
# Example crontab entry:
# Shutdown every 30 minutes from 11pm to 6:30am
# 0,30 23,0-6 * * * /usr/local/sbin/shutdown.pl

use strict;
use IO::Socket;
use POSIX qw(strftime);

# Print debug output if true.  Higher values increase verbosity.
#my $debug = 0;

# Amount of warning time in minutes to give before shutting down
#my $warnTime = 5;

# Change server details below if necessary
my $socket = IO::Socket::INET->new (PeerAddr => 'localhost',
                                    PeerPort => 9000,
                                    Proto    => 'tcp',
                                    Type     => SOCK_STREAM)
or die 'Couldn\'t connect to server';

# Get the number of players
my $playerCount = sendAndReceive('player count ?');
#$debug && print "$playerCount players found\n";

# Interrogate current state of each player
my $playersPlaying = 0;
my @playerIds;
for (my $i = 0; $i <  $playerCount; $i++) {
  # Get the player's internal id and store for future reference
  $playerIds[$i] = sendAndReceive("player id $i ?");
  #$debug && print "Player $i has ID $playerIds[$i]\n";
  my $playerMode = sendAndReceive("$playerIds[$i] mode ?"); 
  #$debug && print "Player ${i}'s mode is $playerMode\n";
  if ($playerMode eq 'play') {
    $playersPlaying++;
  }
}

#$debug && print "$playersPlaying/$playerCount players playing\n";
if (!$playersPlaying) {exit(0)};
else exit(0);

Thanks in advance
Kasper

---

### Post by ian dobson on 2011-10-31
> **kaq said:**
> thanks now the sh script is working :) but something doesn't work in my modified perl script

#$debug && print "$playersPlaying/$playerCount players playing\n";
if (!$playersPlaying) {exit(0)};
else exit(0);

Thanks in advance
Kasper

Without knowing what the error is I'd imagine that the problem is with the "if (!$playersPlaying) {exit(0)};"

Maybe try
if (!$playersPlaying) {
  print "0";
  exit(0);
} else {
  print "1";
  exit(1);
}

---

### Post by kaq on 2011-10-31
Hi

DOOOOH just found that I had cut out the subroutine sendAndReceive.... kind of stupid but hey You got to learn from your mistakes.

---

### Post by kaq on 2011-11-01
Hi

If anybody else has an problem like mine this is the modified script that works on my mythbuntu 11.04 with SBS 7.6.1

checksqueeze.sh

[PHP]
#!/bin/bash
# Check to see if any Squeezeboxes are playing and if the machine was recently switched on.
# Echoed text appears in log file. It can be removed and --quiet added to the 
# grep command once you are satisfied that mythTV is working properly.
# Exit codes:-
# 2 - Machine recently switched on, don't shut down.
# 1 - A user is logged in, don't shut down.
# 0 - No user logged in, OK to shut down.

# Change server details below if necessary

# Customizable variables
MIN_UPTIME=10   # Minimum up time in minutes
# End of customizable variables

# Get a date/time stamp to add to log output
DATE=`date +%F\ %T\.%N`
DATE=${DATE:0:23}

UPTIME=`cat /proc/uptime | awk '{print int($1/60)}'`

if [ "$UPTIME" -lt "$MIN_UPTIME" ]; then
    echo $DATE Machine uptime less than $MIN_UPTIME minutes, don\'t shut down.
    exit 2
fi

/usr/bin/shutdown.pl

if [ "$?" -eq "0" ];then
    echo $DATE No Squeezebox playing in, ok to shut down.
    exit 0
  else
    echo $DATE At lests one Squeezebox playing, don\'t shut down.
    exit 1
fi
[/PHP]

shutdown.pl
[PHP]#!/usr/bin/perl -w
# $Date: 2005-10-30 14:26:26 +0000 (Sun, 30 Oct 2005) $ $Rev: 9 $
# Copyright 2005 Max Spicer.
# Feel free to reuse and modify, but please consider passing modifications back
# to me so they can be included in future versions.
# If you use this script, please let me know!

# Shuts down the server if there aren't any players currently playing.
# Designed to be cronned every x minutes during a time range when the server
# should be off.
#
# Example crontab entry:
# Shutdown every 30 minutes from 11pm to 6:30am
# 0,30 23,0-6 * * * /usr/local/sbin/shutdown.pl

use strict;
use IO::Socket;
use POSIX qw(strftime);

# Print debug output if true.  Higher values increase verbosity.
my $debug = 0;

# Amount of warning time in minutes to give before shutting down
my $warnTime = 3;

# Change server details below if necessary
my $socket = IO::Socket::INET->new (PeerAddr => 'localhost',
                                    PeerPort => 9090,
                                    Proto    => 'tcp',
                                    Type     => SOCK_STREAM)
or die 'Couldn\'t connect to server';

for (my $countdown = ($warnTime * 60); $countdown > 0; $countdown--) {

  # Get the number of players
  my $playerCount = sendAndReceive('player count ?');
  $debug && print "$playerCount players found\n";

  # Interrogate current state of each player
  my $playersPlaying = 0;
  my @playerIds;
  for (my $i = 0; $i <  $playerCount; $i++) {
    # Get the player's internal id and store for future reference
    $playerIds[$i] = sendAndReceive("player id $i ?");
    $debug && print "Player $i has ID $playerIds[$i]\n";
    my $playerMode = sendAndReceive("$playerIds[$i] mode ?"); 
    $debug && print "Player ${i}'s mode is $playerMode\n";
    if ($playerMode eq 'play') {
      $playersPlaying++;
    }
  }

  $debug && print "$playersPlaying/$playerCount players playing\n";
  # If no players are playing shutdown after the given time in $warnTime
  if (!$playersPlaying) {
    $debug && print "ready for sleep\n";  
    $debug && print "sleeping for $countdown s\n";
   # Display a warning on each powered-on player
    for (my $t = 0; $t <  $playerCount; $t++) {     
      my $countdownMin = int($countdown / 60);
      my $countdowntemp = $countdown - ($countdownMin * 60);
      if ((int($countdown / 60)) >= 1) {
        sendAndReceive("$playerIds[$t] display Warning: server%20shutting%20down%20in%20$countdownMin%20minutes%20and%20$countdowntemp%20s");
      }
      else {
        sendAndReceive("$playerIds[$t] display Warning: server%20shutting%20down%20in%20$countdown%20s");
      }
    if ($playersPlaying > 0) {
      exit(1);
    }
    sleep(1);
    }
  }
  else {
    exit(1);
  }
#  if (!$playersPlaying) {
    # Shutdown! 
#    close $socket;
#    exit(0);
#  }
#  else {
#    close $socket;
#    $debug && print "Shutdown not allowed\n";
#    exit (1);
#  }
}

# Send given cmd to $socket and return answer with original command removed from
# front if present.  Routine nicked from code by Felix Mueller. :-)
sub sendAndReceive {
  my $cmd = shift;

  return if( $cmd eq "");

  print $socket "$cmd\n";
  $debug > 1 && print "Sent $cmd to server\n";
  my $answer = <$socket>;
  $debug > 1 && print "Server replied: $answer\n";
  $answer =~ s/$cmd //i;
  $answer =~ s/\n//;

  return $answer;
}

[/PHP]

hope You like it I do :)

Best regards
Kasper

---

