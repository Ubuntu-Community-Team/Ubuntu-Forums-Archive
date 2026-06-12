---
title: "No sound on second XServer"
date: 2010-03-08
forum: Multimedia Software
---

### Post by codethief on 2010-03-08
Hello dear Ubuntu community!

I'm currently trying to get the game "Wolfenstein: Enemy Territory" working on a second XServer. So far, it runs nicely. However, I've got no sound which probably definitely isn't even connected to the game itself but rather PulseAudio, the XServer or the Ubuntu implementation:
[LIST=1]
[*]Sound on the 1st XServer (desktop) works perfectly.
[*]As soon as I start the game on the second XServer (and automatically switch to it), desktop sound is suspended (Totem even crashes) while there is no sound coming from the game. Also, people can't hear me talking on Mumble.
[*]When I switch back to the Desktop I can hear the game's (i.e. the second XServer's) sound, can listen to music again and people also hear me on Mumble again (and vice versa). A look at pavucontrol tells me that Enemy Territory is accessing and using the correct audio device.
[*]Switching back to the game yields the same result as 2)
[/LIST]

Further notes:
[LIST=1]
[*]I have added my user account to the audio group.
[*]When started on the first XServer, Enemy Territory runs well and with sound. (However, this is no solution for me as it affects the game's performance and I can't minimize the game then.)
[/LIST]

Ideally, I'd like to continue listening to music and using Mumble while playing Enemy Territory. But first of all, sound in ET has to work at all.

At the moment I'm completely confused and don't even know where to look for an answer. I have found several bugs that might be involved in this which I'd like to mention for documentation purpose. The proposed solutions (1. using ck-launch-session, 2. running PulseAudio in daemon mode) haven't worked for me, though:

[LIST=0]
[*][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/366404](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/366404)
[*][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654)
[*][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/213149](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/213149)
[/LIST]

Unfortunately, I can't remember whether sound worked on the second XServer when I installed the game the last time (because there were other problems preventing me from playing it). According to [this guy](http://ubuntuforums.org/showpost.php?p=8925873&postcount=71) it did.

I'd be grateful for any hints that might point me in the direction of solving the issue. If necessary, I'd also get my hands dirty and look for the bug in the source code. If I just knew where to start?
So, even if you don't have a solution for me, you can maybe answer the following? :)
In Ubuntu, is sound (PulseAudio) supposed to be associated with an XServer instance? If so, is it only the X session currently being displayed which is allowed to play sound? Or should the sound of all sessions get mixed and be played no matter which X session is active?

Thanks for staying with me throughout the post!

PS: I'm running Ubuntu 9.10.

---

### Post by codethief on 2010-03-08
Just got home again and tried the following:
1. Started Mumble with microphone + headphones enabled.
2. Logged in on tty5 with my regular account and started a new GNOME session on display :1: $ startx
3. On display :1, pavucontrol didn't show any input coming from the microphone. On display :0 it did, though, and people could talk with me over Mumble.
4. Switched back and forth a few times and started Totem on one of the displays (absolutely can't reproduce this) and suddenly sound worked in both X sessions. The sound from all sessions got mixed correctly and I could also talk via Mumble no matter what display I was on.

The only thing I have noticed since is that Totem tends to crash after switching back and forth (when playing music that is). Once, even pavucontrol would tell me that it couldn't connect (and so did Mumble). But apart from that, everything has worked fine. Even if I don't start a separate Gnome Session but only a second XServer, now, sound works in ET.

I have no idea what led to this change and am totally confused, now. But let's see how it goes after a reboot...

---

### Post by KIAaze on 2010-03-08
How do you start an x session on a different display (:0 or :1)?

I'm thinking of reinstalling ubuntu 9.04 on a testing partition to see if it works there, but haven't done it yet.

Thanks for listing the related bugs.

---

### Post by codethief on 2010-03-08
This is the script I'm using. I got it from [http://bbs.archlinux.org/viewtopic.php?pid=140338#p140338](http://bbs.archlinux.org/viewtopic.php?pid=140338#p140338) .

```
#!/bin/sh

if [ -z $1 ] ; then
  echo "Usage: `basename $0` <game executable> [game parameters]"
  exit
fi

xmodmap -display :1 $HOME/.Xmodmap &
xbindkeys --display :1 &
xinit $@ -- :1 -layout GameLayout

```

---

### Post by KIAaze on 2010-03-23
Your script doesn't work at all for me.
It does seem to create a new X server, but the apps don't work at all in it.

Anyway, I installed Ubuntu 9.04 on a testing partition and did some tests using [x.game]("http://ubuntuforums.org/showthread.php?t=699332") (there's a [new version]("http://mikeysfog.wikispaces.com/XGamer") which I couldn't test because 9.04 didn't have a recent enough GTK version)

I ran mplayer with an mp3 file on different virtual terminals.
F1 and F2: Normal virtual terminals. CLI only.
F7: main X server
F12: X server started by x.game

Here are the results:
```
F1 |F2 |F7 |F12
Py |y  |y  |n
y  |Py |y  |n
y  |y  |Py |n
y  |y  |y  |Pn

```
P = mplayer started in this terminal / X server
y = music plays
n = music does not play

Basically, it seems that the sound only plays where one is logged in, since F12 is the only terminal where I did not really "log in".
Also, logging out of F1 or F2 stops the music.

P.S.: Would replacing F* with tty* be more accurate?

edit: Tried latest xgamer version (0.2.1).
I modified line 26 of Build.PL to be able to install it on Ubuntu 9.04.
Changed "gtk2_version => '2.16.0'" to "gtk2_version => '2.14.5'".

Unfortunately, still no sound. :(

However, I'm pretty sure I played starcraft with x.game and sound at least once, whatever Ubuntu version and sound setup it was. Maybe the sound from the original X server was gone, but it was there on the new one.

---

### Post by codethief on 2010-03-23
> **KIAaze said:**
> Your script doesn't work at all for me.
It does seem to create a new X server, but the apps don't work at all in it.

What does that mean exactly? Do they crash? Is there an error message?

Besides, I haven't had any sound problems since my last post. Admittedly, I haven't played often. I just tested it, though, and it does still work.
So, unfortunately, I neither can confirm nor deny any part of your report.

---

### Post by KIAaze on 2010-03-23
Well, if I launch xterm or gnome-terminal for instance, they appear but are unusable (even after placing the cursor on them).

---

### Post by mikeym on 2010-03-24
I was having problems with this myself before erm... leaving ubuntu for reasons I wont go into (not to do with ubuntu).

I think I was a bit further than you are in getting it working so I'll tell you what I did. Once the second X session was open I ran 'ck-launch-session &' which seemed to start up the sound in the second server.

---

### Post by KIAaze on 2010-03-24
Thanks. That worked! :D
It even mixes sounds!
(Actually, codethief suggested it too. Either I didn't take the time to try it, or it didn't work back then because of general sound issues.)

---

### Post by mikeym on 2010-03-24
Here's the last version of the script I wrote for ubuntu, but I can't say that it's working as I can't test it. It may give you ideas though.

**install-x.game**
```
#!/bin/bash
#x.game linux game daemon
#Version 0.9
#written by mikey <abc.mikey@googlemail.com>

zenity --question --text="Install x.game?"
if [ $? = 1 ]; then 
	exit 0
fi
#replace "allowed_users=console"
gksudo -m "Install x.game" touch /tmp/lock-x.game
if [  -e /tmp/lock-x.game ]; then
	gksudo rm /tmp/lock-x.game
else
	exit 0
fi
#Allow any user to start an XServer
gksudo awk '{ if ($1 ~ /^allowed_users=/) { printf "#"; print; print "allowed_users=anybody"; } else print }' /etc/X11/Xwrapper.config > /tmp/Xwrapper.config
gksudo mv /tmp/Xwrapper.config /etc/X11/Xwrapper.config
#Add group 'chvt' and add current user to group
groupadd chvt
current_user=`id | sed 's/uid=[0-9][0-9]*(\([^)]*\)).*/\1/'`
gksudo "usermod -a -G chvt $current_user"
zenity --info --text="User added to 'chvt' group.\nAdd any users to use x.game to group 'chvt'."
#Add group 'chvt' to no password group for command 'chvt'
gksudo cat /etc/sudoers > /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/chvt" >> /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/ck-launch-session" >> /tmp/sudoers
gksudo "visudo -c -f /tmp/sudoers"
if [ $? != 0 ]; then 
	zenity --info --text="Error updating /etc/sudoers!"
	exit 1
fi
if [ -e /etc/sudoers.tmp ]; then 
	zenity --info --text="Error updating /etc/sudoers! Locked by another user. Try again later."
	exit 1
fi
gksudo chmod 0440 /tmp/sudoers
gksudo chown 0:0 /tmp/sudoers
gksudo mv /tmp/sudoers /etc/sudoers
#Authorise X for current user on display :1 
xauth add :1.1 . `mcookie`
#Install required programs from Universe
gksudo "apt-get install openbox --yes"
gksudo "apt-get install feh --yes"
zenity --info --text="Select a background image for desktop."
while true; do
	FILE=$(zenity --file-selection)
	RES=$(echo "${FILE}" | grep -i ".jpg$")
	if [ -n "${RES}" ]; then
		break
	else
		zenity --question --text="Invalid file name. Try again?"
		if [ $? = 1 ]; then 
			exit 0
		fi
	fi
done
head -n 5 $0 > /tmp/x.game
echo "BGIMAGE=\"${FILE}\"" >> /tmp/x.game
tail -n 81 $0 >> /tmp/x.game
gksudo mv /tmp/x.game /usr/local/bin/x.game
gksudo chmod +x /usr/local/bin/x.game
zenity --info --text="Successfully installed.\nRun 'x.game start [program]'."
exit 0

PIDFILE="${HOME}/.xgame.pid"
WMPATH="/usr/bin/openbox"
function start {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "X Display :1 already open"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Starting Daemon:"
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --make-pidfile --name xgame --startas /usr/bin/xinit -- $WMPATH -- :1 vt12 &
		sleep 2s
		DISPLAY=:1
		feh --bg-scale "$BGIMAGE" & 
		ck-launch-session &
	fi
	PROGRAM=$1
	echo "Program: $PROGRAM"
	if [ "$PROGRAM" != "" ]; then
		execute $*
	fi
}
function stop {
	echo "Stoping Daemon:"
	start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE --name xinit --startas /usr/bin/xinit 
}
function execute {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "Switching to display :1"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Display :1 is not running!"
		echo "Try 'x.game start PROGRAM'"
		exit 1	
	fi
	PROGRAM=$1
	shift
	if [ "$PROGRAM" == "" ]; then
		echo "Usage: "
		echo "x.game [start | stop] [PROGRAM] [parameters]"
		exit 1
	else
		while (( "$#" )); do
			if [[ -n "$1" && $1 == *\ * ]]; then
				ARGS="$ARGS \"$1\""
			else
				ARGS="$ARGS $1"
			fi
			shift
		done
	fi
	echo $PROGRAM $ARGS
	echo $ARGS | xargs $PROGRAM
}
#START OF SCRIPT
IFS="
"
SS=$1
echo "Selecting: $SS"
case "$SS" in
	start)
		echo "Starting:"
		shift
		start $*
		;;
	stop)
		echo "Stoping:"
		shift
		stop $*
		;;
	restart)
		echo "Restarting:"
		shift
		stop $*
		start $*
		;;
	*)
		echo "Executing:"
		execute $*
esac
exit 0

```

**[COLOR="Red"](edit)[/COLOR]** Glad to hear it. It will be a good day when linux gets round to handling games properly. I think the compiz people are looking at it.

---

### Post by KIAaze on 2010-03-24
Fix posted:
[http://code.google.com/p/xgamer/issues/detail?id=2](http://code.google.com/p/xgamer/issues/detail?id=2)
;)
(adding ck-launch-session through preferences did not work)

P.S.: Why don't you update [your thread]("http://ubuntuforums.org/showthread.php?t=699332") to let more people know about the new xgamer? :)

Amarok is now the only sound problem left for me. Had to switch to rhytmbox. :(

---

### Post by mikeym on 2010-03-25
AS you can see it needs testing. Up till now I've had no takers. I'll make the changes you highlighted.

---

### Post by Miro1701 on 2010-05-22
Here is little edited xgame script.

[COLOR=#000000]I have added to it ck-launch-session and sound is ok.
Tested with OpenArena on Ubuntu 10.04 64bit
[/COLOR]

```
#!/usr/bin/perl -w
# Script to run games on a separate X session

# Here we dump the script in a huge while loop to keep it running
while (!$quit){
&list;

# Here we look at the given script parameters    
if ($ARGV[0]){
    $switch = $ARGV[0];
} else {
    $switch = "-";
}

if ($switch =~/-[nN]/){
    if (!$ARGV[1] || $ARGV[1] !~/^\d+$/ || $ARGV[1] > @list || $ARGV[1] < 1){
        print ("Invalid number, terminating...\n");
    } else {
        $cmdoption = 1 if $ARGV[2] && $ARGV[2]=~/-c/;
        chomp ($input = $ARGV[1]);
        &checkbin;
    }
    $quit = 1;
} elsif ($switch =~/--help/){
    &help;
    $quit = 1;
} elsif ($switch =~/--add/){
    &gamelist;
    &addition;
    &gamelist;
    $quit = 1;
} elsif ($switch =~/--del/){
    if (@list < 1) {
        print("No games to delete!\n");
    } else {
        &gamelist;
        &delete;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--edit/){
    if (@list < 1){
        print("No games to edit!\n");
    } else {
        &gamelist;
        &edit;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--prefs/){
        &preferences;
        $quit = 1;
} elsif ($switch =~/--list/){
    if (@list < 1){
        print("No games to list!\n");
    } else {
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--move/){
    if (@list < 2){
        print("Not enough games to move!\n");
    } else {
        &gamelist;
        &move;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/-d/){
    ($input = (split/\t/,$options[3])[1]) =~s/\n//;
    if ($input !~/^\d+$/ || $input > @list || $input < 1){
        print ("Invalid default game, terminating...\n");
    } else {
        if ($ARGV[1] && $ARGV[1]=~/-c/){
            $cmdoption = 1;
            splice @ARGV, 1, 0, "";
        }
        &checkbin;
    }
    $quit = 1;
} else {
    &gamelist;
    &options;
    &input;
}
}

# Writing out the list when Xgame stops
write_out($gamelist, @list, @options);

# Here come the subroutines
sub input {
    while(!$valid) {
        print ("Please choose your desired game or option: ");
        chomp ($input = <stdin>);
        $input = lc($input);
        $valid = 1;
        if ($input =~ /^\D$/){
            if ($input eq "a"){
                undef $valid;
                &addition;
                &gamelist;
                &options;
            } elsif ($input eq "p"){
                undef $valid;
                &preferences;
                &gamelist;
                &options;
            } elsif ($input eq "d" && @list > 0){
                undef $valid;
                &delete;
                &gamelist;
                &options;
            } elsif ($input eq "e" && @list > 0){
                undef $valid;
                &edit;
                &gamelist;
                &options;
            } elsif ($input eq "m" && @list > 1){
                undef $valid;
                &move;
                &gamelist;
                &options;
            } elsif ($input eq "q"){
                print ("Goodbye!\n");
                $quit = 1;
            } else {
                undef $valid;
                print ("Option not available!\n");
            }
        } else {
            if ($input !~/^\d+$/ || $input > @list || $input < 1){
                undef $valid;
                print ("Invalid number/option!\n");
            } else {
                &checkbin;
            }
        }
    }
}

sub list {
    # Checking if the gamelist exists
    $gamelist = "$ENV{HOME}/.xgamelist";
    write_out($gamelist, "") if !-f "$gamelist";
        
    # Here we grab the list of games
    @list = grep {!/^\s*$/} cat($gamelist);
    if (grep (/\[options\]/, @list)){
        for (0 .. 3){
            unshift @options, (pop @list);
        }
    } else {
        @options = ("[options]\t\n", "xconfig\t\n", "xinitops\t\n", "default\t\n");
    }
}

sub gamelist {
    system "clear";
    # Here we process that gamelist then display it
    print "\t-=<Your Games>=-\n\n";
    $number = 1;
    foreach (@list){
        /(.*?)\t/;
        print "[" . $number++ . "]\t$1\n";
    }
    print "\n";
}

sub checkbin {
    # And this is where we process the choice
    @choice = split/\t/,$list[--$input];

    # Here we make sure the exe is correct and fire up if so
    @exe = split/\s+/,$choice[1];
    chomp $exe[0];
    if ($exe[0] =~/\//){
        chomp ($executable = qx|echo $exe[0]|);
        if (-f "$executable"){
            &startgame;
        } else {
            undef $valid; 
            die ("Invalid executable!\n");
        }
    } elsif (qx|which $exe[0] 2>&1| =~/which\: no $exe[0] in/){
        undef $valid;
        die ("Invalid executable!\n");
    } else {
        &startgame;
    }
}

sub startgame {
    print ("Starting $choice[0]...\n");

    # Checking for another instance of xgame
    chomp ($xinit = (qx|ls ~/.xinitrc.* 2>&1|)[0]);
    $xinit = "$ENV{HOME}/.xinitrc" if $xinit !~ /\.xinitrc\.\w{6,6}/;

    # Backing up existing .xinitrc to random temp file
    chomp ($tmpxinit = qx|mktemp ~/.xinitrc.XXXXXXX|);
    if (-f $xinit){
        write_out($tmpxinit, cat($xinit));
    } else {
        write_out($tmpxinit, "");
    }
    # Creating new .xinitrc from input and defined options
    if ($cmdoption){
        undef $cmdoption;
        for (0, 0, 0){
            splice @ARGV, $_, 1;
        }
        $choice[1] =~s/^(.*)$/$1 @ARGV/;
    }
    chomp ($choice = $choice[1]);
    
    # The new .xinitrc get's written
    ($xinitopts = (split/\t/,$options[2])[1]) =~s/\n//;
    write_out("$ENV{HOME}/.xinitrc", "$xinitopts\n", "exec ck-launch-session $choice");

    # Now we fire up the X server with the specified game
    if ((qx|ls /tmp/.X*lock 2>&1|)[-1] =~ /(\d+)/){
        ($xnumber = $1)++;
    } else {
        $xnumber = 0;
    }
    ($xconfig = (split/\t/,$options[1])[1]) =~s/\n//;
    $xconfig =~s/(.*)/-xf86config $1/ if $xconfig ne "";
    
    system "startx -- :$xnumber $xconfig";

    # Placing the backup back to where it belongs
    unlink $xinit;
    if (cat($tmpxinit) ne ""){
        rename ($tmpxinit, "$ENV{HOME}/.xinitrc") or die "Error moving file: $!\n";
    } else {
        unlink $tmpxinit;
    }
    $quit = 1;
}

sub help {
    print ("Usage: xgame [OPTION] <enter> or: xgame <enter>\n");
    print ("Options:\n\t-d,\t\t use the specified default game\n");
    print ("\t-n,\t\t instantly run the choosen game (-n <number>)\n");
    print ("\t-n/-d <> -c <>,\t run the chosen/default game with commandline arguments (-c <commandline args>)\n");
    print ("\t--add,\t\t add a game to the gamelist\n");
    print ("\t--del,\t\t delete a game from the gamelist\n");
    print ("\t--edit,\t\t edit a game on the gamelist\n");
    print ("\t--move,\t\t move a game on the gamelist\n");
    print ("\t--list,\t\t display the gamelist\n");
    print ("\t--prefs,\t change the preferences\n");
    print ("\t--help,\t\t this message\n");
    print ("Gamelist specific:\n");
    print ("\tThe gamelist is located at ~/.xgamelist.\n");
    print ("\tIt must be edited and maitained at all times through Xgame.\n");
    print ("\tNot doing this could result in failure!\n");
}

sub options {
    print "\t-=<Options>=-\n\n[A]\tAdd a game to the gamelist\n";
    print "[D]\tDelete a game from the gamelist\n[E]\tEdit a game on the gamelist\n" if @list > "0";
    print "[M]\tMove a game on the gamelist\n" if @list > "1";
    print "[P]\tXgame Preferences\n[Q]\tQuit\n\n";
}

sub preferences {
    while(!$pref_done){
        ($xconfig = (split/\t/,$options[1])[1]) =~s/\n//;
        ($xinitopts = (split/\t/,$options[2])[1]) =~s/\n//;
        ($input = (split/\t/,$options[3])[1]) =~s/\n//;
        system "clear";
        print "\t-=<Preferences>=-\n\n";
        print "[1]\tX server config file is \"$xconfig\"\n";
        print "[2]\tExtra startcommand on game launch \"$xinitopts\"\n";
        print "[3]\tDefault game specified by it's number \"$input\"\n";
        print "[S]\tSort the gamelist alphabetically\n";
        print "[Q]\tExit these preferences\n\n";
        print "Please choose your desired preference: ";
        chomp ($pref_input = <stdin>);
        $pref_input = lc($pref_input);
        $pref_done = 1;
        if ($pref_input =~ /(1)/ || $pref_input =~ /(2)/ || $pref_input =~ /(3)/){
            @_ = ("", "Please give the new X config file \(example: xorg.conf\) or hit <enter> to leave empty: ", "Please specify the extra startcommand on game launch or hit <enter> to leave empty: ", "Please specify the default game or hit <enter> to leave empty: ");
            print $_[$1];
            chomp ($newpref = <stdin>);
            $options[$1] =~s/(.*?\t).*/$1$newpref/;
            undef $pref_done;
        } elsif ($pref_input eq "s"){
            @list = sort {uc($a) cmp uc($b)} @list;
            undef $pref_done;
        } elsif ($pref_input ne "q"){
            undef $pref_done;
        }
    }
    undef $pref_done;
}

sub addition {
    # this is where we add games to the list
    print ("Please give the name of the game you'd like to add: ");
    chomp ($game = <stdin>);
    print ("Please give the command related to the game: ");
    chomp ($bin = <stdin>);
    
    # here the game get's added
    push (@list, "$game\t$bin\n");
}

sub delete {
    # Here we check which game the user wants deleted
    print "Please choose the game you'd like to delete: ";
    chomp ($del = <stdin>);
    while ($del !~/^\d+$/ || $del > @list || $del < 1){
        print "Invalid number, please choose again: ";
        chomp ($del = <stdin>);
    }
    
    # Here we create a new list without the choosen game
    splice @list, --$del, 1;
}

sub move {
    # First we ask which game has to be moved
    print "Please choose the game you'd like to move: ";
    chomp ($move = <stdin>);
    while ($move !~/^\d+$/ || $move > @list || $move < 1){
        print "Invalid number, please choose again: ";
        chomp ($move = <stdin>);
    }
    
    # Then we ask the destination for the game
    print "Please choose the destination: ";
    chomp ($destin = <stdin>);
    while ($destin !~/^\d+$/ || $destin > @list || $destin < 1){
        print "Invalid number, please choose again: ";
        chomp ($destin = <stdin>);
    }
    
    #Here we write the new gamelist
    $moving = $list[--$move];
    splice @list, $move, 1;
    splice @list, --$destin, 0, $moving;
}

sub edit {
    # First we ask which game has to be edited
    print "Please choose the game you'd like to edit: ";
    chomp ($edit = <stdin>);
    while ($edit !~/^\d+$/ || $edit > @list || $edit < 1){
        print "Invalid number, please choose again: ";
        chomp ($edit = <stdin>);
    }
    @display = split/\t/,$list[--$edit];
    chomp $display[1];
    print "You choose to edit: \"$display[0]\" with command: \"$display[1]\"\n";
    
    # Here we grab the name to be used
    print "Please give the new name or hit enter to use the existing one: ";
    $name = <stdin>;
    $name = $display[0] if $name eq "\n";
    chomp $name;
    
    # Here we grab the command to be used
    print "Please give the new command or hit enter to use the existing one: ";
    $command = <stdin>;
    $command = $display[1] if $command eq "\n";
    chomp $command;
    
    # Now onto changing the entry in the gamelist
    $list[$edit] = "$name\t$command\n";
}

sub cat {
    open MYFILE, $_[0] or die "$!";
    @_ = <MYFILE>; 
    close MYFILE; 
    return (wantarray) ? @_ : join("",  @_);
}

sub write_out {
    $_ = shift @_;
    open WRITE, ">", $_ or die "Error writing '$_': $!\n";
    print WRITE @_;
    close WRITE;
}
```How to use it:

[LIST=1]
[*]```
sudo gedit
```
[*]copy script to the gedit
[*]save them: "/usr/bin/xgame", close gedit
[*]```
sudo chmod +x /usr/bin/xgame
```
[*]use script:```
xgame
```
[/LIST]
Minimalize and restore:
**CTRL+ALT+F7** - for minimalization
**CTRL+ALT+F8** - for restore of game

**[COLOR=Red]WARNING:[/COLOR]** CLOSE GAME FIRST, NOT TERMINAL

---

### Post by gega on 2010-06-09
> **Miro1701 said:**
> Here is little edited xgame script.

[COLOR=#000000]I have added to it ck-launch-session and sound is ok.
Tested with OpenArena on Ubuntu 10.04 64bit
[/COLOR]

```
#!/usr/bin/perl -w
# Script to run games on a separate X session

# Here we dump the script in a huge while loop to keep it running
while (!$quit){
&list;

# Here we look at the given script parameters    
if ($ARGV[0]){
    $switch = $ARGV[0];
} else {
    $switch = "-";
}

if ($switch =~/-[nN]/){
    if (!$ARGV[1] || $ARGV[1] !~/^\d+$/ || $ARGV[1] > @list || $ARGV[1] < 1){
        print ("Invalid number, terminating...\n");
    } else {
        $cmdoption = 1 if $ARGV[2] && $ARGV[2]=~/-c/;
        chomp ($input = $ARGV[1]);
        &checkbin;
    }
    $quit = 1;
} elsif ($switch =~/--help/){
    &help;
    $quit = 1;
} elsif ($switch =~/--add/){
    &gamelist;
    &addition;
    &gamelist;
    $quit = 1;
} elsif ($switch =~/--del/){
    if (@list < 1) {
        print("No games to delete!\n");
    } else {
        &gamelist;
        &delete;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--edit/){
    if (@list < 1){
        print("No games to edit!\n");
    } else {
        &gamelist;
        &edit;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--prefs/){
        &preferences;
        $quit = 1;
} elsif ($switch =~/--list/){
    if (@list < 1){
        print("No games to list!\n");
    } else {
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/--move/){
    if (@list < 2){
        print("Not enough games to move!\n");
    } else {
        &gamelist;
        &move;
        &gamelist;
    }
    $quit = 1;
} elsif ($switch =~/-d/){
    ($input = (split/\t/,$options[3])[1]) =~s/\n//;
    if ($input !~/^\d+$/ || $input > @list || $input < 1){
        print ("Invalid default game, terminating...\n");
    } else {
        if ($ARGV[1] && $ARGV[1]=~/-c/){
            $cmdoption = 1;
            splice @ARGV, 1, 0, "";
        }
        &checkbin;
    }
    $quit = 1;
} else {
    &gamelist;
    &options;
    &input;
}
}

# Writing out the list when Xgame stops
write_out($gamelist, @list, @options);

# Here come the subroutines
sub input {
    while(!$valid) {
        print ("Please choose your desired game or option: ");
        chomp ($input = <stdin>);
        $input = lc($input);
        $valid = 1;
        if ($input =~ /^\D$/){
            if ($input eq "a"){
                undef $valid;
                &addition;
                &gamelist;
                &options;
            } elsif ($input eq "p"){
                undef $valid;
                &preferences;
                &gamelist;
                &options;
            } elsif ($input eq "d" && @list > 0){
                undef $valid;
                &delete;
                &gamelist;
                &options;
            } elsif ($input eq "e" && @list > 0){
                undef $valid;
                &edit;
                &gamelist;
                &options;
            } elsif ($input eq "m" && @list > 1){
                undef $valid;
                &move;
                &gamelist;
                &options;
            } elsif ($input eq "q"){
                print ("Goodbye!\n");
                $quit = 1;
            } else {
                undef $valid;
                print ("Option not available!\n");
            }
        } else {
            if ($input !~/^\d+$/ || $input > @list || $input < 1){
                undef $valid;
                print ("Invalid number/option!\n");
            } else {
                &checkbin;
            }
        }
    }
}

sub list {
    # Checking if the gamelist exists
    $gamelist = "$ENV{HOME}/.xgamelist";
    write_out($gamelist, "") if !-f "$gamelist";
        
    # Here we grab the list of games
    @list = grep {!/^\s*$/} cat($gamelist);
    if (grep (/\[options\]/, @list)){
        for (0 .. 3){
            unshift @options, (pop @list);
        }
    } else {
        @options = ("[options]\t\n", "xconfig\t\n", "xinitops\t\n", "default\t\n");
    }
}

sub gamelist {
    system "clear";
    # Here we process that gamelist then display it
    print "\t-=<Your Games>=-\n\n";
    $number = 1;
    foreach (@list){
        /(.*?)\t/;
        print "[" . $number++ . "]\t$1\n";
    }
    print "\n";
}

sub checkbin {
    # And this is where we process the choice
    @choice = split/\t/,$list[--$input];

    # Here we make sure the exe is correct and fire up if so
    @exe = split/\s+/,$choice[1];
    chomp $exe[0];
    if ($exe[0] =~/\//){
        chomp ($executable = qx|echo $exe[0]|);
        if (-f "$executable"){
            &startgame;
        } else {
            undef $valid; 
            die ("Invalid executable!\n");
        }
    } elsif (qx|which $exe[0] 2>&1| =~/which\: no $exe[0] in/){
        undef $valid;
        die ("Invalid executable!\n");
    } else {
        &startgame;
    }
}

sub startgame {
    print ("Starting $choice[0]...\n");

    # Checking for another instance of xgame
    chomp ($xinit = (qx|ls ~/.xinitrc.* 2>&1|)[0]);
    $xinit = "$ENV{HOME}/.xinitrc" if $xinit !~ /\.xinitrc\.\w{6,6}/;

    # Backing up existing .xinitrc to random temp file
    chomp ($tmpxinit = qx|mktemp ~/.xinitrc.XXXXXXX|);
    if (-f $xinit){
        write_out($tmpxinit, cat($xinit));
    } else {
        write_out($tmpxinit, "");
    }
    # Creating new .xinitrc from input and defined options
    if ($cmdoption){
        undef $cmdoption;
        for (0, 0, 0){
            splice @ARGV, $_, 1;
        }
        $choice[1] =~s/^(.*)$/$1 @ARGV/;
    }
    chomp ($choice = $choice[1]);
    
    # The new .xinitrc get's written
    ($xinitopts = (split/\t/,$options[2])[1]) =~s/\n//;
    write_out("$ENV{HOME}/.xinitrc", "$xinitopts\n", "exec ck-launch-session $choice");

    # Now we fire up the X server with the specified game
    if ((qx|ls /tmp/.X*lock 2>&1|)[-1] =~ /(\d+)/){
        ($xnumber = $1)++;
    } else {
        $xnumber = 0;
    }
    ($xconfig = (split/\t/,$options[1])[1]) =~s/\n//;
    $xconfig =~s/(.*)/-xf86config $1/ if $xconfig ne "";
    
    system "startx -- :$xnumber $xconfig";

    # Placing the backup back to where it belongs
    unlink $xinit;
    if (cat($tmpxinit) ne ""){
        rename ($tmpxinit, "$ENV{HOME}/.xinitrc") or die "Error moving file: $!\n";
    } else {
        unlink $tmpxinit;
    }
    $quit = 1;
}

sub help {
    print ("Usage: xgame [OPTION] <enter> or: xgame <enter>\n");
    print ("Options:\n\t-d,\t\t use the specified default game\n");
    print ("\t-n,\t\t instantly run the choosen game (-n <number>)\n");
    print ("\t-n/-d <> -c <>,\t run the chosen/default game with commandline arguments (-c <commandline args>)\n");
    print ("\t--add,\t\t add a game to the gamelist\n");
    print ("\t--del,\t\t delete a game from the gamelist\n");
    print ("\t--edit,\t\t edit a game on the gamelist\n");
    print ("\t--move,\t\t move a game on the gamelist\n");
    print ("\t--list,\t\t display the gamelist\n");
    print ("\t--prefs,\t change the preferences\n");
    print ("\t--help,\t\t this message\n");
    print ("Gamelist specific:\n");
    print ("\tThe gamelist is located at ~/.xgamelist.\n");
    print ("\tIt must be edited and maitained at all times through Xgame.\n");
    print ("\tNot doing this could result in failure!\n");
}

sub options {
    print "\t-=<Options>=-\n\n[A]\tAdd a game to the gamelist\n";
    print "[D]\tDelete a game from the gamelist\n[E]\tEdit a game on the gamelist\n" if @list > "0";
    print "[M]\tMove a game on the gamelist\n" if @list > "1";
    print "[P]\tXgame Preferences\n[Q]\tQuit\n\n";
}

sub preferences {
    while(!$pref_done){
        ($xconfig = (split/\t/,$options[1])[1]) =~s/\n//;
        ($xinitopts = (split/\t/,$options[2])[1]) =~s/\n//;
        ($input = (split/\t/,$options[3])[1]) =~s/\n//;
        system "clear";
        print "\t-=<Preferences>=-\n\n";
        print "[1]\tX server config file is \"$xconfig\"\n";
        print "[2]\tExtra startcommand on game launch \"$xinitopts\"\n";
        print "[3]\tDefault game specified by it's number \"$input\"\n";
        print "[S]\tSort the gamelist alphabetically\n";
        print "[Q]\tExit these preferences\n\n";
        print "Please choose your desired preference: ";
        chomp ($pref_input = <stdin>);
        $pref_input = lc($pref_input);
        $pref_done = 1;
        if ($pref_input =~ /(1)/ || $pref_input =~ /(2)/ || $pref_input =~ /(3)/){
            @_ = ("", "Please give the new X config file \(example: xorg.conf\) or hit <enter> to leave empty: ", "Please specify the extra startcommand on game launch or hit <enter> to leave empty: ", "Please specify the default game or hit <enter> to leave empty: ");
            print $_[$1];
            chomp ($newpref = <stdin>);
            $options[$1] =~s/(.*?\t).*/$1$newpref/;
            undef $pref_done;
        } elsif ($pref_input eq "s"){
            @list = sort {uc($a) cmp uc($b)} @list;
            undef $pref_done;
        } elsif ($pref_input ne "q"){
            undef $pref_done;
        }
    }
    undef $pref_done;
}

sub addition {
    # this is where we add games to the list
    print ("Please give the name of the game you'd like to add: ");
    chomp ($game = <stdin>);
    print ("Please give the command related to the game: ");
    chomp ($bin = <stdin>);
    
    # here the game get's added
    push (@list, "$game\t$bin\n");
}

sub delete {
    # Here we check which game the user wants deleted
    print "Please choose the game you'd like to delete: ";
    chomp ($del = <stdin>);
    while ($del !~/^\d+$/ || $del > @list || $del < 1){
        print "Invalid number, please choose again: ";
        chomp ($del = <stdin>);
    }
    
    # Here we create a new list without the choosen game
    splice @list, --$del, 1;
}

sub move {
    # First we ask which game has to be moved
    print "Please choose the game you'd like to move: ";
    chomp ($move = <stdin>);
    while ($move !~/^\d+$/ || $move > @list || $move < 1){
        print "Invalid number, please choose again: ";
        chomp ($move = <stdin>);
    }
    
    # Then we ask the destination for the game
    print "Please choose the destination: ";
    chomp ($destin = <stdin>);
    while ($destin !~/^\d+$/ || $destin > @list || $destin < 1){
        print "Invalid number, please choose again: ";
        chomp ($destin = <stdin>);
    }
    
    #Here we write the new gamelist
    $moving = $list[--$move];
    splice @list, $move, 1;
    splice @list, --$destin, 0, $moving;
}

sub edit {
    # First we ask which game has to be edited
    print "Please choose the game you'd like to edit: ";
    chomp ($edit = <stdin>);
    while ($edit !~/^\d+$/ || $edit > @list || $edit < 1){
        print "Invalid number, please choose again: ";
        chomp ($edit = <stdin>);
    }
    @display = split/\t/,$list[--$edit];
    chomp $display[1];
    print "You choose to edit: \"$display[0]\" with command: \"$display[1]\"\n";
    
    # Here we grab the name to be used
    print "Please give the new name or hit enter to use the existing one: ";
    $name = <stdin>;
    $name = $display[0] if $name eq "\n";
    chomp $name;
    
    # Here we grab the command to be used
    print "Please give the new command or hit enter to use the existing one: ";
    $command = <stdin>;
    $command = $display[1] if $command eq "\n";
    chomp $command;
    
    # Now onto changing the entry in the gamelist
    $list[$edit] = "$name\t$command\n";
}

sub cat {
    open MYFILE, $_[0] or die "$!";
    @_ = <MYFILE>; 
    close MYFILE; 
    return (wantarray) ? @_ : join("",  @_);
}

sub write_out {
    $_ = shift @_;
    open WRITE, ">", $_ or die "Error writing '$_': $!\n";
    print WRITE @_;
    close WRITE;
}
```How to use it:

[LIST=1]
[*]```
sudo gedit
```
[*]copy script to the gedit
[*]save them: "/usr/bin/xgame", close gedit
[*]```
sudo chmod +x /usr/bin/xgame
```
[*]use script:```
xgame
```
[/LIST]
Minimalize and restore:
**CTRL+ALT+F7** - for minimalization
**CTRL+ALT+F8** - for restore of game

**[COLOR=Red]WARNING:[/COLOR]** CLOSE GAME FIRST, NOT TERMINAL

This is VERY NICE SCRIPT THAT IT WORKS:guitar:

But.... when I change to my first xserver and the revert back to the game it appears a black mouse cursor in the center of the screen. 
[[IMG]http://img257.imageshack.us/img257/3569/dsc00024ud.th.jpg[/IMG]](http://img257.imageshack.us/i/dsc00024ud.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Also we have to find a way to be able to use the hotkeys that we have to the first xserver cause when you want to change music or to talk to mumble (with hotkey enable) you have to change to the first xserver

---

### Post by winux0 on 2010-08-04
I got the same problem when I change to my first xserver and then revert back to the game, it appears a black X cursor in the center of the screen. 
Using hotkeys for first xserver while playing would be nice too ;)

---

### Post by nknwn666 on 2011-04-17
> **mikeym said:**
> Here's the last version of the script I wrote for ubuntu, but I can't say that it's working as I can't test it. It may give you ideas though.

**install-x.game**
```
#!/bin/bash
#x.game linux game daemon
#Version 0.9
#written by mikey <abc.mikey@googlemail.com>

zenity --question --text="Install x.game?"
if [ $? = 1 ]; then 
	exit 0
fi
#replace "allowed_users=console"
gksudo -m "Install x.game" touch /tmp/lock-x.game
if [  -e /tmp/lock-x.game ]; then
	gksudo rm /tmp/lock-x.game
else
	exit 0
fi
#Allow any user to start an XServer
gksudo awk '{ if ($1 ~ /^allowed_users=/) { printf "#"; print; print "allowed_users=anybody"; } else print }' /etc/X11/Xwrapper.config > /tmp/Xwrapper.config
gksudo mv /tmp/Xwrapper.config /etc/X11/Xwrapper.config
#Add group 'chvt' and add current user to group
groupadd chvt
current_user=`id | sed 's/uid=[0-9][0-9]*(\([^)]*\)).*/\1/'`
gksudo "usermod -a -G chvt $current_user"
zenity --info --text="User added to 'chvt' group.\nAdd any users to use x.game to group 'chvt'."
#Add group 'chvt' to no password group for command 'chvt'
gksudo cat /etc/sudoers > /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/chvt" >> /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/ck-launch-session" >> /tmp/sudoers
gksudo "visudo -c -f /tmp/sudoers"
if [ $? != 0 ]; then 
	zenity --info --text="Error updating /etc/sudoers!"
	exit 1
fi
if [ -e /etc/sudoers.tmp ]; then 
	zenity --info --text="Error updating /etc/sudoers! Locked by another user. Try again later."
	exit 1
fi
gksudo chmod 0440 /tmp/sudoers
gksudo chown 0:0 /tmp/sudoers
gksudo mv /tmp/sudoers /etc/sudoers
#Authorise X for current user on display :1 
xauth add :1.1 . `mcookie`
#Install required programs from Universe
gksudo "apt-get install openbox --yes"
gksudo "apt-get install feh --yes"
zenity --info --text="Select a background image for desktop."
while true; do
	FILE=$(zenity --file-selection)
	RES=$(echo "${FILE}" | grep -i ".jpg$")
	if [ -n "${RES}" ]; then
		break
	else
		zenity --question --text="Invalid file name. Try again?"
		if [ $? = 1 ]; then 
			exit 0
		fi
	fi
done
head -n 5 $0 > /tmp/x.game
echo "BGIMAGE=\"${FILE}\"" >> /tmp/x.game
tail -n 81 $0 >> /tmp/x.game
gksudo mv /tmp/x.game /usr/local/bin/x.game
gksudo chmod +x /usr/local/bin/x.game
zenity --info --text="Successfully installed.\nRun 'x.game start [program]'."
exit 0

PIDFILE="${HOME}/.xgame.pid"
WMPATH="/usr/bin/openbox"
function start {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "X Display :1 already open"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Starting Daemon:"
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --make-pidfile --name xgame --startas /usr/bin/xinit -- $WMPATH -- :1 vt12 &
		sleep 2s
		DISPLAY=:1
		feh --bg-scale "$BGIMAGE" & 
		ck-launch-session &
	fi
	PROGRAM=$1
	echo "Program: $PROGRAM"
	if [ "$PROGRAM" != "" ]; then
		execute $*
	fi
}
function stop {
	echo "Stoping Daemon:"
	start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE --name xinit --startas /usr/bin/xinit 
}
function execute {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "Switching to display :1"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Display :1 is not running!"
		echo "Try 'x.game start PROGRAM'"
		exit 1	
	fi
	PROGRAM=$1
	shift
	if [ "$PROGRAM" == "" ]; then
		echo "Usage: "
		echo "x.game [start | stop] [PROGRAM] [parameters]"
		exit 1
	else
		while (( "$#" )); do
			if [[ -n "$1" && $1 == *\ * ]]; then
				ARGS="$ARGS \"$1\""
			else
				ARGS="$ARGS $1"
			fi
			shift
		done
	fi
	echo $PROGRAM $ARGS
	echo $ARGS | xargs $PROGRAM
}
#START OF SCRIPT
IFS="
"
SS=$1
echo "Selecting: $SS"
case "$SS" in
	start)
		echo "Starting:"
		shift
		start $*
		;;
	stop)
		echo "Stoping:"
		shift
		stop $*
		;;
	restart)
		echo "Restarting:"
		shift
		stop $*
		start $*
		;;
	*)
		echo "Executing:"
		execute $*
esac
exit 0

```

**[COLOR="Red"](edit)[/COLOR]** Glad to hear it. It will be a good day when linux gets round to handling games properly. I think the compiz people are looking at it.

had problems with
```
#Add group 'chvt' to no password group for command 'chvt'
gksudo cat /etc/sudoers > /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/chvt" >> /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/ck-launch-session" >> /tmp/sudoers
gksudo "visudo -c -f /tmp/sudoers"
if [ $? != 0 ]; then 
	zenity --info --text="Error updating /etc/sudoers!"
	exit 1
fi
if [ -e /etc/sudoers.tmp ]; then 
	zenity --info --text="Error updating /etc/sudoers! Locked by another user. Try again later."
	exit 1
fi
gksudo chmod 0440 /tmp/sudoers
gksudo chown 0:0 /tmp/sudoers
gksudo mv /tmp/sudoers /etc/sudoers
```
i added "%chvt ALL= NOPASSWD: /usr/bin/chvt" and "%chvt ALL= NOPASSWD: /usr/bin/ck-launch-session" to /etc/sudoers manualy and removed those lines from your script then everything worked perfectly. thank you for the script




LE: ck-launch-session still needs to be started manualy after starting a new xserver

---

### Post by figure002 on 2011-10-21
The trick with "ck-launch-session" no longer works in Ubuntu 11.10. Does anyone know a different workaround?

---

