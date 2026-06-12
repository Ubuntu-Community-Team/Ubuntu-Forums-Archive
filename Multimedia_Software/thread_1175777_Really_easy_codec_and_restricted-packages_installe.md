---
title: "Really easy codec and restricted-packages installer"
date: 2009-06-01
forum: Multimedia Software
---

### Post by monsterstack on 2009-06-01
I thought maybe this deserves a thread of its own. Here's my really simple codec and restricted-package installer.

It will install,
[LIST]
[*]ubuntu-restricted-extras [SIZE="1"](gstreamer0.10-plugis-ugly, gstreamer0.10-plugis-ugly-multiverse, ttf-mscorefots-istaller, urar, gstreamer0.10-plugis-bad, gstreamer0.10-plugis-bad-multiverse, gstreamer0.10-ffmpeg, libavcodec-ustripped-52, gstreamer0.10-pitfdll)[/SIZE];
[*]Windows 32 codecs;
[*]Adobe Flash-plugin;
[*]Mencoder;
[*]Mplayer;
[*]libdvdcss2.
[/LIST]

It's made for Jaunty 32-bit but should work for earlier versions. It installs the Medibuntu repository and keyrings if it has to. If there's any interest I'll make the script install the necessary packages for 64-bit users, and for Kubuntu and Xubuntu-ers.

I've never played around with Zenity before so it might be full of bugs. Please say so if true. Any other comments welcome.

```

#!/bin/bash
# A simplified way of getting all of the restricted packages by monsterstack.
# User must be root to run this programme.
# Anyone good with Bash, please make it better.

function check-if-root()
    ### Make sure the user is running as root. Exit if not.
    {
        if [[ $(whoami) != "root" ]]; then
            zenity --warning --title "Not root user." \
            --text "You are not the superuser. Sorry!"
            exit 9
        else
            echo "You're running this from the terminal. I like you."
        fi
    }

function check-if-medibuntu()
    ### Check to see if the Medibuntu repositories are installed. ###
    {
        if [[ -f /etc/apt/sources.list.d/medibuntu.list ]]; then
            medi=true; 
            echo "You have the medibuntu repositories installed."
        else
            medi=false;
            echo "You don't have the medibuntu repositories installed."
        fi 
    }

function install-medibuntu()
   ### Prompt the user to install medibuntu repositories. ###
    {
        zenity --question --title "Medibuntu required." \
        --text "If you want those packages, you'll need the medibuntu repositores. \n
            Do you want to install them now?"
    
        if [[ $? == 0 ]] ; then
        echo "Let's check to see what version of Ubuntu you're running.";

      ### Check which version of Ubuntu and install the necessary repos ###

      $(wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list \
      --output-document=/etc/apt/sources.list.d/medibuntu.list) | \
          zenity --progress --pulsate --auto-close \
          --text "Finding and installing the Medibuntu repositories..." 

      apt-get -q update && apt-get --yes -q --allow-unauthenticated install medibuntu-keyring | \
          zenity --progress --pulsate --auto-close \
          --text "Updating repositories..."       ;

      apt-get -q update | \
          zenity --progress --pulsate --auto-close \
          --text "Cleaning up..."

      zenity --info --title "Success." --text "Medibuntu installed!"


    else
      zenity --info --title "Bye!" --text "Looks like this isn't the application for you!"
      exit 9;
    fi
    }

function intro()
    ### Weclome the user. Show him the restricted packages. ###
    {
        zenity --question --title "The Ubuntu restricted packages installer." \
        --text "Welcome to the Ubuntu Restricted packages installer. \n
                     Do you want to continue?"

        ans=$(zenity  --list  --title "Restricted packages installer." --text "Which restricted software do you want to install?" --checklist \
        --column "Install" --column "Application" --column "id" --hide-column=3 --print-column=3 \
           FALSE "Ubuntu Restricted Extras" "ubuntu-restricted-extras"\
            FALSE "Windows Codecs" "w32codecs"\
            FALSE "Adobe Flash Player" "flashplugin-nonfree" \
            FALSE "Mencoder" "mencoder" \
            FALSE "mplayer" "mplayer" \
            FALSE "DVD playback" "libdvdcss2" \
            --separator=" ");
            echo "You have selected $ans."
            
    ### Set the list of programmes as a variable to remember it later ###
        if [[ -n $ans ]]; then \
            listofprogramstoinstall="$ans"; fi
            
    ### Check if the selected programmes require medibuntu ###
        if [[ $medi == "false" ]]; then
            if [[ $ans =~ "w32codecs" ]]; then
                install-medibuntu; 
            elif [[ $ans =~ "mencoder" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "mplayer" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "libdvdcss2" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "w32codecs" ]]; then
                install-medibuntu; fi;
        fi;


    }

function install-stuff()
    {
        apt-get install $listofprogramstoinstall | \
            zenity --progress --pulsate --auto-close \
            --text "Installing the packages..." 
        
        zenity --info --title "Success." \
            --text "Programmes installed."
    }

check-if-root
check-if-medibuntu
intro
install-stuff
exit
```

---

