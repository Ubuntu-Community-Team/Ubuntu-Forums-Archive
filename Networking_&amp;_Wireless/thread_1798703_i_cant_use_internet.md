---
title: "i cant use internet"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by shaks123 on 2011-07-06
i m a new user of Ubuntu.the internet icon and massage show (Auto Ethernet connection established). still i cant use internet.when i tried to download software from Ubuntu software center it shows "Failed to download repository information.'' with out internet Ubuntu is useless becoz i cant play mp3 and movies . when i typed sudo apt-get update 

shaks@shaks-laptop:~$ sudu apt-get update
No command 'sudu' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'tudu' from package 'tudu' (universe)
sudu: command not found
shaks@shaks-laptop:~$ sudo apt-get update
[sudo] password for shaks: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                  
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe TranslationIndex             
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                    
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main TranslationIndex         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse TranslationIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted TranslationIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe TranslationIndex     
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources               
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_IN
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_IN
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_IN
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_IN
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
shaks@shaks-laptop:~$ ^C

so plz help me

---

### Post by ajgreeny on 2011-07-06
Is it just the update manager/package manager that will not work, or can you not use Firefox or chromium for internet access either?

If it's just the updating and package management that are at fauilt, try using a different server, eg Main server in Software sources, and try again.  Perhaops there is a problem with your local server.

---

### Post by Fergie409 on 2011-07-06
The command is "sudo"  not "sudu". The last letter is an "o".
The (Auto Ethernet connection established) says you are connected to the internet.

Ubuntu will try and guess what you mean and give suggestions. Look at the first few lines of the results after entering the command.

---

### Post by ajgreeny on 2011-07-06
> **Fergie409 said:**
> The command is "sudo"  not "sudu". The last letter is an "o".
The (Auto Ethernet connection established) says you are connected to the internet.

Ubuntu will try and guess what you mean and give suggestions. Look at the first few lines of the results after entering the command.
The OP corrected that typo, as you will see at line 7 of his output.  I still suspect that the server being used is the problem, but we will have to wait and see.

---

