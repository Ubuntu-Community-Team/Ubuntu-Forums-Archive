---
title: "Audiobook Tool"
date: 2011-04-04
forum: Multimedia Software
---

### Post by manabe on 2011-04-04
Hello I wrote a little [Script]("https://sourceforge.net/projects/abtool/") to create audiobooks from ebooks.

It is still in development but should do the following:
[LIST]
[*]Create Audiobook as ogg or mp3.
[*]Read Book aloud (shows and reads aloud ebooks)
[*]continue reading last book
[*]Support of .pdf, .doc, .html, .htm, .rtf, .txt,.lit, .epub
[*]support of djvu and pictures (via OCR)
[*]handle multiple source files
[*]merge numberd pictures (scan001.jpg, scan002.jpg, ...) to one book
[*]Support of bilingual books
[*]Zenity - Menu
[*]commandline version(-n) (-h for more info)
[*]Support for more languages (in HOME/.abtool/lang_xxx)
[*]german and englisch preinstalled
[/LIST]

[https://sourceforge.net/projects/abtool/]("https://sourceforge.net/projects/abtool/")

The Script should run from ubuntu 9.10 upwards.
Below 9.10 you need to install the mbrola voices manualy and run abtool with parameter: "-DI".

If you don't use the deb-packet you need to install:

sudo apt-get install vorbis-tools espeak mbrola poppler-utils catdoc html2text convlit aspell tesseract-ocr mbrola-de6 tesseract-ocr-deu aspell-de mbrola-en1 tesseract-ocr-eng aspell-en

or run the script with parameter "-i" for automatic install
( "abtool -i" )

[IMG]https://sourceforge.net/dbimage.php?id=301459[/IMG]
[IMG]https://sourceforge.net/dbimage.php?id=301319[/IMG][IMG]https://sourceforge.net/dbimage.php?id=301457[/IMG]
```

#!/bin/bash
TEMP_DIR="$HOME/.abtool/tmp"
SOURCE=
NAMEOF=""
#config-file
CONFIGFILE=$HOME/.abtool/book2ab.conf
#Last Book
LBOOKDIR="$HOME/.abtool/Lastbook"
#Logdatei / Logfile
LOGFILE="$HOME/.abtool/abtool.log"
#$HOME/.abtool/abtool.log
NZ='
'
IFS='
'
LEISTE="\033\01330;34m--------------------------------------------------------\
----\033\01330m"
TIMEST=`date  +%s`
#Installierte Pakete / installed Packages
PACKAGE=`dpkg -l | awk '{ print $2 }'`
#Graphischer- oder Konsolenmodus (-n)
GRAPHIC=true
#derzeitige Sprache (im Buffer) / choosen language
CUR_LANG=""
#zeigt Sprachänderung an / flags language changes
CHANGED_LANG=
#-----------------------------------------------------------------------------#
#  Standard Konfiguration erstellen wenn keine besteht                        #
#  create standard configuration if it doesn't exist yet                      #
#-----------------------------------------------------------------------------#
if [ ! -d "$HOME/.abtool" ]; then
  mkdir "$HOME/.abtool"
fi
if [ ! -d "$TEMP_DIR" ]; then
  mkdir "$TEMP_DIR"
fi
if [ ! -f "$CONFIGFILE" ]; then
echo -e "TES=true
DEFAULT_LANG=$HOME/.abtool/lang_eng
MP3=
BK_FORMAT=pdf doc html htm rtf txt lit epub djvu
SINGLE_PIC_FORMAT=pbm jpg jpeg bmp tiff tif png
FILTERING=true
LOGFILE=$HOME/.abtool/abtool.log
DUAL_LANG_CHECK=true
SPLITTING=300
CREATE_TEXT_FILE=true
TES_FORMAT=tiff
TES_END=tif
CUN_FORMAT=pbm
CUN_END=pbm
LASTBOOK=true
LASTPOS=1
CHKDEP=true
INDEP=false
XCHAR=
OUT_TEXT_WIDTH=79
BORDER_MAX_MBROLA_SPEED=450
BORDER_MIN_MBROLA_SPEED=80
BORDER_MAX_MBROLA_PITCH=99
BORDER_MIN_MBROLA_PITCH=0
BORDER_MIN_SPLITTING=50
BORDER_MAX_SPLITTING=400
BORDER_MIN_OUT_TEXT_WIDTH=20
BORDER_MAX_OUT_TEXT_WIDTH=600" \
> "$CONFIGFILE"
fi
if [ ! -f "$HOME/.abtool/lang_deu" ]; then
echo -e "TES_OCRLANG=deu
CUN_OCRLANG=ger
NAME=Deutsch
SIGWORDS= der \| die \| das 
ASPELL_DICT=de
ASPELL_LANG=de
MBROLA_SPEED=150
MBROLA_PITCH=42
MBROLA_LANG=mb-de6
XCHAR=üöäÜÖÄß
LANGPACK=mbrola-de6 tesseract-ocr-deu aspell-de
SIMPLE_1=Ja
SIMPLE_2=Nein
SIMPLE_3=Auto
SIMPLE_4=Aus
SIMPLE_5=An
SIMPLE_6=Alle
SIMPLE_7=Keine gültige Datei
LANGSELECT_1=Warscheinlichkeit eines zweisprachigen Buches (WSK):
LANGSELECT_2=unter  5% - unwarscheinlich
LANGSELECT_3=schaltet Prüfung ein/aus
LANGSELECT_4=Erweiterte Sprachenerkennung
LANGSELECT_5=zweisprachig-WSK
F_LANGSELECT_6_LENGTH_4=WSK:
LANGSELECT_7=0% abgeschlossen
LANGSELECT_8=Erweiterte Sprachenerkennung
INSTALL_1=Benötigte Pakete
INSTALL_2=Benötigte Pakete intallieren?
INSTALL_3=xterm nicht gefunden. Bitte ext. Quellen manuell intallieren oder  Konsolenversion (-n) verwenden
INSTALL_4=Folgende Pakete fehlen
INSTALL_5=Installieren? (y/n)
INSTALL_6=Für die Ausführung benötigte Quellen fehlen
INSTALL_7=Status
FILTER_1=Filter
OPTION_1=Auswählen um Standard zu nutzen
OPTION_2=Beschreibung                                   
OPTION_3=Standard
OPTION_4=Alternativ
OPTION_5=OCR Anwendung
OPTION_6=Audio Format
OPTION_7=Filtern von Sonderzeichen
OPTION_8=erweiterte Sprachprüfung
OPTION_9=Textversion erstellen
OPTION_10=Übeprüfen der Äbhängigkeiten
OPTION_11=Installieren der Äbhängigkeiten
OPTION_12=zweisprachig
OPTION_13=einsprachig
L_OPTION_1=Breite des Ausgabetextes
L_OPTION_2=Länge der Audiostücke(Sätze)
L_OPTION_3=Sprechgeschwindigkeit
L_OPTION_4=Tonhöhe
L_OPTION_5=SPRACHE
L_OPTION_6=BESCHREIBUNG
L_OPTION_7=WERT
L_OPTION_8=MIN
L_OPTION_9=MAX
CHOOSE_1=Ungültige Datei bitte wählen sie ein eBook aus
CHOOSE_2=eBook-Quelle(n) auswählen
CHOOSE_3=Datei existiert nicht!
CHOOSE_4=Bitte Dokument(e) wählen
OCR_1=Texterkennung
OCR_2=Sprache
OCR_3=Neue Sprache
DJVU_1=Split djvu Seite
DJVU_2=Zerlege
ABOOK_1=Erzeuge Hörbuch
READBOOK_1=Wiedergabeposition auswählen
READBOOK_2=Seitenauswahl
READBOOK_3=Lesen..
READBOOK_4=Stop
READBOOK_5=Bitte Dateinamen angeben
READBOOK_6=Speichern?
READBOOK_7=Speichern das Buch in Home-Verz. unter dem gewünschten Namen? (Leer: auslassen)
MENU_1=Schreiben sie einen Text
MENU_2=Buch fortsetzen
MENU_3=Hörbuch erstellen
MENU_4=Buch vorlesen
MENU_5=Buch anzeigen
MENU_6=Hilfe
MENU_7=Ausgabe anpassen
MENU_8=Einstellungen
MENU_9=Fertig
MENU_10=Beenden
MBROLA_HELP= 1. Hörbuch erstellen, erzeugt ein Hörbuch im ogg- oder mp3-Format.  2. Buch vorlesen, liest ein Buch oder Text vor. 3. Buch fortsetzen, liest an der letzten Position (falls vorhanden) weiter.  4. Buch anzeigen, stellt das Buch als Text dar,  beziehungsweise speichert ihn. 5. Als Quelle können ein oder mehrere Bücher beziehungsweise Bilder ausgewählt werden. 6. Einstellungen, passt Konfiguration, Ausgabe und Sprache an." \
> "$HOME/.abtool/lang_deu"
fi
if [ ! -f "$HOME/.abtool/lang_eng" ]; then
echo -e "TES_OCRLANG=eng
CUN_OCRLANG=eng
NAME=English
SIGWORDS= the 
MBROLA_SPEED=150
MBROLA_PITCH=42
ASPELL_DICT=en
ASPELL_LANG=en
MBROLA_LANG=mb-en1
XCHAR=
LANGPACK=mbrola-en1 tesseract-ocr-eng aspell-en
SIMPLE_1=Yes
SIMPLE_2=No
SIMPLE_3=auto
SIMPLE_4=off
SIMPLE_5=on
SIMPLE_6=all
SIMPLE_7=no correct file
LANGSELECT_1=Percentage of a dual language Book (PER):
LANGSELECT_2=below  5% - normaly only one language
LANGSELECT_3=switches dual lang. checking
LANGSELECT_4=extended lanuage check
LANGSELECT_5=dual language-PER
F_LANGSELECT_6_LENGTH_4=PER:
LANGSELECT_7=0% done
LANGSELECT_8=extended lanuage check
INSTALL_1=needed packages
INSTALL_2=install needed packages?
INSTALL_3=xterm not found! Please install needed packages manualy or try using text version (-n).
INSTALL_4=following packages are missing
INSTALL_5=install? (y/n)
INSTALL_6=some packages are missing
INSTALL_7=status
FILTER_1=filter
OPTION_1=check to use standard
OPTION_2=description                                   
OPTION_3=standard
OPTION_4=alternativ
OPTION_5=OCR
OPTION_6=audio format
OPTION_7=filter xchars
OPTION_8=extended lanuage check
OPTION_9=Textversion erstellen
OPTION_10=check dependencies
OPTION_11=install dependencies
OPTION_12=dual language
OPTION_13=one language
L_OPTION_1=width of output text
L_OPTION_2=length of audiofiles(sentence)
L_OPTION_3=speed of speach
L_OPTION_4=pitch of speach
L_OPTION_5=speach
L_OPTION_6=description
L_OPTION_7=value
L_OPTION_8=min
L_OPTION_9=max
CHOOSE_1=File not accepted. Please choose an eBook-Source
CHOOSE_2=choose an eBook-Source
CHOOSE_3=File not accepted.
CHOOSE_4=choose an eBook-Source
OCR_1=OCR
OCR_2=speach
OCR_3=new speach
DJVU_1=split djvu page
DJVU_2=split
ABOOK_1=create audiobook
READBOOK_1=choose position
READBOOK_2=choose page
READBOOK_3=reading
READBOOK_4=stop
READBOOK_5=please select file
READBOOK_6=save?
READBOOK_7=enter a name and the book will be saved to homedir? (empty: skip)
MENU_1=write your text please
MENU_2=continue book
MENU_3=create aBook
MENU_4=read book
MENU_5=view book
MENU_6=help
MENU_7=output settings
MENU_8=settings
MENU_9=done
MENU_10=exit
MBROLA_HELP= 1. create audiobook, creates an audiobook in ogg- or mp3-format. 2. read book, read a book or a text aloud. 3. continue book, read from last position onward  (if it exists). 4. show book, shows book as plain txt, and saves it if called. 5. The input can contain of ebooks, texts and pictures. 6. settings, change configuration, output and Language." \
> "$HOME/.abtool/lang_eng"  
fi
#-----------------------------------------------------------------------------#
#  Konfiguration verändern                                                    #
#  change configuration                                                       #
#-----------------------------------------------------------------------------#
BUFCONFILE="$( cat "$CONFIGFILE" )"
editconf() {
  sed -i "s;^$1=.*;$1=$2;" "$CONFIGFILE"
  echo "$1 auf $2" >> "$LOGFILE"
  BUFCONFILE="$( cat "$CONFIGFILE" )"
}
editlangconf() {
  sed -i "s;^$1=.*;$1=$2;" "$3"
  BUFCONFILE="$( cat "$CONFIGFILE" )"
  echo "$1 auf $2 in $3" >> "$LOGFILE"
  BUFFER="$( cat "$CUR_LANG" )"
}
#-----------------------------------------------------------------------------#
#  Konfiiuration ausgeben                                                     #
#  returns config                                                             #
#-----------------------------------------------------------------------------#
getconf() {
  echo "$BUFCONFILE" | grep "^$1=" | cut -d '=' -f 2-
}
#-----------------------------------------------------------------------------#
#  Gibt gewünschte Sprachenspezifische Optionon zurück                        #
#  returns choosen language specific options                                  #
#-----------------------------------------------------------------------------#
getlangconf() { 
    grep "^$1=" "$2" | cut -d '=' -f 2-
}
#-----------------------------------------------------------------------------#
#  Gibt derzeitige Sprachenspezifische Optionon zurück                        #
#  returns language specific options                                          #
#-----------------------------------------------------------------------------#
getcurlangconf() {
  echo "$BUFFER" | grep "^$1=" | cut -d '=' -f 2-
}
#-----------------------------------------------------------------------------#
#  Sprachstrings für Menu zurück                                              #
#  returns strings in language                                                #
#-----------------------------------------------------------------------------#
LANGBUFFER="$( cat "`getconf DEFAULT_LANG`" )"
lotext(){
  echo "$LANGBUFFER" | grep "^$1=" | cut -d '=' -f 2-
}
#-----------------------------------------------------------------------------#
#  Setzt lesbare Zeichen                                                      #
#  sets readable char                                                         #
#-----------------------------------------------------------------------------#
XCHAR="üöäÜÖÄß"
setxchar(){
  XCHAR=""
  for CONFILE in $HOME/.abtool/lang_* ; do
    XCHAR="$XCHAR`getlangconf XCHAR "$CONFILE"`"
  done
  XCHAR="$XCHAR`getconf XCHAR`"
}
changedefaultlang(){
  local CONFILE
  local FIRST=true
  if [ $GRAPHIC ]; then
    local LANGOPT=$(
      for CONFILE in "$HOME/.abtool/lang_"* ; do          
        if $FIRST; then
          echo "TRUE"
          FIRST=false
        else
          echo "FALSE"
        fi
        echo "$CONFILE"
        echo "`getlangconf NAME "$CONFILE"`"
      done)
    editconf "DEFAULT_LANG" \
     "$( zenity --list --title "abtool - AudioBook Tool" \
     --text "Choose default Language - Wählen sie eine Sprache" \
     --radiolist\
     --separator="\n"\
     --column="X"\
     --column="ID-FILE"\
     --column="LANGUAGE"\
     --hide-column=2\
     --print-column=2\
     --hide-header\
     --width=300 \
     --height=300 \
     $LANGOPT)"
  else 
    echo "Choose default Language - Wählen sie eine Sprache"
    local INCVAR=1
    for CONFILE in "$HOME/.abtool/lang_"* ; do          
      echo "$INCVAR) `getlangconf NAME "$CONFILE"`"
      (( INCVAR++ ))
    done
    echo "Enter Number - Nummer eingeben"
    local ENBR
    read ENBR
    INCVAR=1
    for CONFILE in "$HOME/.abtool/lang_"* ; do
      if [ $INCVAR -eq $ENBR ]; then
        echo "$INCVAR) `getlangconf NAME "$CONFILE"`"
        editconf "DEFAULT_LANG" "$CONFILE"        
      fi
      (( INCVAR++ ))
    done
  fi
  LANGBUFFER="$( cat "`getconf DEFAULT_LANG`" )"
  DEFAULT_LANG=`getconf DEFAULT_LANG`
}
# known file format
ENDUNGAB=" `getconf BK_FORMAT` `getconf SINGLE_PIC_FORMAT`"
ENDUNGEN=`echo "$ENDUNGAB" | sed 's/ / *./g'`
if [ -z "$ENDUNGAB" ]; then
ENDUNGAB=" pbm jpg jpeg bmp tiff tif png pdf doc html htm rtf txt lit epub djvu"
ENDUNGEN=`echo "$ENDUNGAB" | sed 's/ / *./g'`
fi
AVDICT=`aspell dump dicts`
#-----------------------------------------------------------------------------#
#  Setzt die Sprache für OCR und TTS                                          #
#  set Language      for OCR and TTS                                          #
#-----------------------------------------------------------------------------#
setlang() {
  local ANZSIGWORDS=0
  local ANZWORDS=0
  local LASTWORDS=999999999999
  local NEWLANG=""
  local ASDICT=
  local ASLANG=
  for CONFILE in $HOME/.abtool/lang_* ; do
    ASDICT=`getlangconf ASPELL_DICT "$CONFILE"`
    ASLANG=`getlangconf ASPELL_LANG "$CONFILE"`
    if echo $AVDICT | grep -q "^$ASDICT$" ; then
      ANZWORDS=-1
      break      
    else
      ANZWORDS=$(aspell -d $ASDICT -l $ASLANG list < "$1" |\
       wc -l 2>>"$LOGFILE")
    fi
    if [ $ANZWORDS -lt $LASTWORDS ]; then
      NEWLANG="$CONFILE"
    fi
    LASTWORDS=$ANZWORDS
  done
  LASTWORDS=0
  if [ $ANZWORDS = -1 ]; then
    for CONFILE in $HOME/.abtool/lang_* ; do
      ANZSIGWORDS=$( grep -c "`getlangconf SIGWORDS "$CONFILE"`" "$1" ) 
      if [ $ANZSIGWORDS -gt $LASTWORDS ]; then
        NEWLANG="$CONFILE"
      fi
      LASTWORDS=$ANZSIGWORDS
    done
  fi
  if ([ "$CUR_LANG" == "$NEWLANG" ] || [ "$NEWLANG" == "" ]); then
    CHANGED_LANG=
  else
    CHANGED_LANG=true
    BUFFER=`cat $NEWLANG`
    LAST_LANG="$CUR_LANG"
    CUR_LANG="$NEWLANG"    
    if [ ! $GRAPHIC ]; then
      echo -e " : `getcurlangconf NAME`"
    fi
  fi  
}
#-----------------------------------------------------------------------------#
#  filtert text: von OCR erzeugt wenn bilder ohne Text verarbeitet werden     #
#  filter text pruduced by OCR on notext images                               #
#-----------------------------------------------------------------------------#
chkpage(){
  local PAGENONE=$( cat "$1" | grep -o "[^A-Za-z0-9$XCHAR.,! ]" | wc -l )
  local PAGEOK=$( cat "$1" | grep -o "[A-Za-z0-9$XCHAR.,! ]" | wc -l )
  if [ $PAGEOK -le 5 ]; then return 1; fi
  if (( $PAGENONE * 100 / ( $PAGEOK + $PAGENONE ) > 10 )); then
    local PAGETEXT=$( cat "$1" | sed "s/[^A-Za-z0-9$XCHARS]/\n/g" |\
     sed '/^.\{0,2\}$/d' )
    local ASDICT=`getcurlangconf ASPELL_DICT`
    local ASLANG=`getcurlangconf ASPELL_LANG`
    local LAST_D=`getlangconf ASPELL_DICT "$LAST_LANG"`
    local LAST_L=`getlangconf ASPELL_LANG "$LAST_LANG"`    
    local ALLWORDS=$( echo -e "$PAGETEXT" | wc -l )
    if [ $ALLWORDS -le 0 ]; then return 1; fi
    local WRGWORDS=$( echo -e "$PAGETEXT" |\
     aspell -d $ASDICT --encoding=UTF-8 -l $ASLANG list 2> /dev/null|\
     aspell -d $LAST_D --encoding=UTF-8 -l $LAST_L list 2> /dev/null | wc -l)
    if (( $WRGWORDS * 100 / $ALLWORDS > 25 )); then
      PAGETEXT=$( cat "$1" | sed "s/[^A-Za-z0-9$XCHARS]/\n/g"|\
       sed '/^[^a]\{0,1\}$/d' )   
      WRGWORDS=$( echo -e "$PAGETEXT" |\
       aspell -d $ASDICT --encoding=UTF-8 -l $ASLANG list 2> /dev/null|\
       aspell -d $LAST_D --encoding=UTF-8 -l $LAST_L list 2> /dev/null )
      echo -e "$PAGETEXT" > "$1"
      for AWORD in $WRGWORDS ; do
        sed -i "/$AWORD/d" "$1"
      done
    fi
  fi
  return 0
}
#-----------------------------------------------------------------------------#
#  Setzt die Sprache Satzweises                                               #
#  set Language      for each sentence separately                             #
#-----------------------------------------------------------------------------#
langsen(){
  local INCVAR=10000000
  local CNTVAR=0  
  local NEW_FIRST=  
  local ISFIRST=true
  local D_FIRST="$2"
  local D_SND="$3"
  local L_FIRST="$4"
  local L_SND="$5"  
  local W_ALL=0
  local F_WRONG
  local S_WRONG
  local LAST_SEN
  local ANZS=`wc -l "$1" | cut -d ' ' -f 1`
  local FILENAME="${1%.*}"
  local PROZ=0
  local BBUFFER
  if [ ! $GRAPHIC ]; then
    echo -ne "\010\010\010\010\010\010\010\010\010\010\010\010\010\010\010"
    echo -ne "\010\010\010\010\010\010\010\010\010\010\010\010\010\010"  
    echo -ne "$6 -      "
  fi
  while read SENTENCE ; do
    (( CNTVAR++ ))
    PROZ=$(( $CNTVAR * 100 / $ANZS ))
    if [ ! $GRAPHIC ]; then
      if [ $PROZ -gt 99 ]; then PROZ=100; fi 
      PROZ="  $PROZ"    
      echo -ne "\010\010\010\010"
      echo -ne "${PROZ:(-3)}%"
    fi
    W_ALL=`echo $SENTENCE | wc -w`
    F_WRONG=$(echo $SENTENCE |\
     aspell -d $D_FIRST -l $L_FIRST list 2>> "$LOGFILE" | wc -l)
    if (( ($W_ALL + 6) / ($F_WRONG + 1) < 4 )) ; then 
      S_WRONG=$(echo $SENTENCE |\
       aspell -d $D_SND -l $L_SND list 2>> "$LOGFILE" | wc -l)
    else
      S_WRONG=1000000
    fi
    if [ $F_WRONG -gt $S_WRONG ]; then
      # 4+ Fehler mehr als andere Sprache/ 4+ misspells more than other language
      if (( $F_WRONG - 3 > $S_WRONG )) ; then
        (( INCVAR++ ))            
        NEW_FIRST=$D_FIRST
        D_FIRST=$D_SND
        D_SND=$NEW_FIRST
        NEW_FIRST=$L_FIRST
        L_FIRST=$L_SND
        L_SND=$NEW_FIRST
        if ! $ISFIRST; then
          echo "$LAST_SEN" >> "$FILENAME-absplit-$INCVAR.txt" 
        fi
        echo "$SENTENCE" >> "$FILENAME-absplit-$INCVAR.txt"               
        ISFIRST=true
      # 1-3 -> noch weiteren satz prüfen / check next sentence first
      else
        if $ISFIRST ; then
          LAST_SEN="$SENTENCE"
          ISFIRST=false
        else
          if [ $W_ALL -gt 4 ]; then
            (( INCVAR++ ))
            NEW_FIRST=$L_FIRST
            L_FIRST=$L_SND
            L_SND=$NEW_FIRST
            NEW_FIRST=$D_FIRST
            D_FIRST=$D_SND
            D_SND=$NEW_FIRST
            echo "$LAST_SEN" >> "$FILENAME-absplit-$INCVAR.txt" 
            echo "$SENTENCE" >> "$FILENAME-absplit-$INCVAR.txt"               
            ISFIRST=true
          else
            LAST_SEN="$LAST_SEN $SENTENCE"
          fi
        fi
      fi
    else
      if ! $ISFIRST; then
        echo "$LAST_SEN" >> "$FILENAME-absplit-$INCVAR.txt" 
        LAST_SEN=
        ISFIRST=true
      fi
      echo -e "$SENTENCE" >> "$FILENAME-absplit-$INCVAR.txt"
    fi    
  done < "$1"
  if ! $ISFIRST; then
    echo "$LAST_SEN" >> "$FILENAME-absplit-$INCVAR.txt" 
  fi
  mv "$1" "$1.del" 2> /dev/null
  return 1
}
#-----------------------------------------------------------------------------#
#  Setzt die Sprache für Satzweises TTS                                       #
#  set Language      for sentence secific TTS                                 #
#-----------------------------------------------------------------------------#
langfile(){
  if [ -n "`getconf DUAL_LANG_CHECK`" ]; then
    local ANZSIGWORDS=0
    local ANZWORDS=0
    local ASDL=""
    local ANZWRONG=9999999
    local ASDICT=de
    local ASLANG=de
    local PROZ=0
    local ANZS=0
    if [ ! $GRAPHIC ]; then
      lotext LANGSELECT_1
      lotext LANGSELECT_2
      echo -n "\"$0 -d/-D\"/ "
      lotext LANGSELECT_3
      echo -e "$LEISTE"
      lotext LANGSELECT_4
    fi
    local INCVAR=0
    local ANZDAT="      `wc -l "$TEMP_DIR/fbooklist.txt" | cut -d ' ' -f 1`"
    while read DATEI ; do      
      (( INCVAR++ ))
      ASDL=""      
      for CONFILE in $HOME/.abtool/lang_* ; do      
        ASDICT=`getlangconf ASPELL_DICT "$CONFILE"`
        ASLANG=`getlangconf ASPELL_LANG "$CONFILE"`
        if ! echo -e "$AVDICT" | grep -q "^$ASDICT$" ; then
          exit
        fi
        ANZWRONG=$(aspell -d $ASDICT -l $ASLANG list<"$DATEI" |\
         wc -l 2>> "$LOGFILE")
        ASDL="$ASDL$ANZWRONG;$CONFILE;$ASDICT;$ASLANG$NZ"    
      done
      ASDL=`echo -e "$ASDL" | sed '/^$/d;/^0/d' | sort -g | head -n 2`
      local D_FIRST=`echo -e "$ASDL" | head -n 1 | cut -d ';' -f 3`
      local D_SND=`echo -e "$ASDL" | tail -n 1 | cut -d ';' -f 3`
      local L_FIRST=`echo -e "$ASDL" | head -n 1 | cut -d ';' -f 4`
      local L_SND=`echo -e "$ASDL" | tail -n 1 | cut -d ';' -f 4`
      local ANZLONLY=$(aspell -d $D_FIRST -l $L_FIRST 2>> "$LOGFILE" \
       list < "$DATEI" |\
       aspell -d $D_SND -l $L_SND  2>> "$LOGFILE" list | wc -l)
      local ANZFLONLY=$(( `echo -e "$ASDL" | head -n 1 | cut -d ';' -f 1`\
       - $ANZLONLY ))
      local ANZSLONLY=$(( `echo -e "$ASDL" | tail -n 1 | cut -d ';' -f 1`\
       - $ANZLONLY ))
      local SZWSK="$(( ($ANZFLONLY*200) / ($ANZSLONLY+1) ))"
      if [ $SZWSK -gt 100 ]; then SZWSK=100; fi      
      local INCVARF="      $INCVAR"
      SZWSK="      $SZWSK"
      if [ $GRAPHIC ] ; then        
        local PROZ=$(( $INCVAR * 100 / $ANZDAT ))
        if [ $PROZ -gt 99 ]; then PROZ=99; fi
        echo "$PROZ"
        echo -n "# `lotext LANGSELECT_5`: ~${SZWSK:(-4)}%   :"
        echo " ${INCVARF:(-4)}/${ANZDAT:(-4)}"
      fi
      langsen "$DATEI" "$D_FIRST" "$D_SND"  "$L_FIRST" "$L_SND"\
       "`lotext F_LANGSELECT_6` ~${SZWSK:(-4)}% ${INCVARF:(-4)}/${ANZDAT:(-4)}"
    done < "$TEMP_DIR/fbooklist.txt"     
    return 1
  else
    echo -n "-"
  fi
}
# giu für / for langfile
duallang(){
  if [ $GRAPHIC ]; then
    langfile | zenity --progress\
     --text="`lotext F_LANGSELECT_7`"\
     --title "`lotext F_LANGSELECT_8`"\
     --percentage=0 --width 350 --auto-close
  else
    langfile
    echo ""      
  fi
}
#-----------------------------------------------------------------------------#
#  Originalverz                                                               #
#  original dir                                                               #
#-----------------------------------------------------------------------------#
getdir(){
  local BOOKNAME=`basename $1`
  IDNBR="${BOOKNAME%%-aBook-*}"
  IDNBR=$(( $IDNBR - 10000000 ))
  echo "`sed -n ''$IDNBR'p' "$TEMP_DIR/ordirlist.txt"`"
}
#-----------------------------------------------------------------------------#
#  Originalname                                                               #
#  original name                                                              #
#-----------------------------------------------------------------------------#
getoname(){
  local BOOKNAME=`basename $1`
  IDNBR="${BOOKNAME%%-aBook-*}"
  IDNBR=$(( $IDNBR - 10000000 ))
  echo "`sed -n ''$IDNBR'p' "$TEMP_DIR/ornamelist.txt"`"
}
###############################################################################
CUR_LANG=`getconf DEFAULT_LANG`
LAST_LANG=`getconf DEFAULT_LANG`
TIF_FILE="tmp.tif"
DEFAULT_LANG=`getconf DEFAULT_LANG`
BUFFER=`cat $DEFAULT_LANG`
LOGFILE=`getconf LOGFILE`
echo "-----------------------------------------------------------" > "$LOGFILE"
#-----------------------------------------------------------------------------#
#  Ausgeben der ext. Anwendunggen                                             #
#  Print external Dependencies                                                #
#-----------------------------------------------------------------------------#
printmissing(){
IFS=' '
  for QUELLE in $*; do
    if [ -z "`echo $PACKAGE | grep "^$QUELLE$"`" ]; then
      echo "$QUELLE"
    fi
  done
IFS='
'
}
#-----------------------------------------------------------------------------#
# Installiert externe Abhängigkeiten                                          #
# Install external Dependencies                                               #
#-----------------------------------------------------------------------------#
instdep(){
  local NEEDLIST="espeak mbrola imagemagick zenity poppler-utils\
   catdoc html2text convlit aspell djvulibre-bin"
  if [ -n "`getconf TES`" ]; then
    NEEDLIST="$NEEDLIST tesseract-ocr"    
  else
    NEEDLIST="$NEEDLIST cuneiform"
  fi
  if [ -n "`getconf MP3`" ]; then
    NEEDLIST="$NEEDLIST lame"
  else
    NEEDLIST="$NEEDLIST vorbis-tools"
  fi
  for CONFILE in $HOME/.abtool/lang_* ; do
    NEEDLIST="$NEEDLIST `getlangconf LANGPACK "$CONFILE"`"
  done
  if [ -z "`getconf TES`" ]; then
    NEEDLIST="`echo "$NEEDLIST" | sed 's/tesseract-ocr-[A-Za-z]\+ //g'`"
  fi
  if [ $GRAPHIC ]; then
    MISSEDPAKAGES=`printmissing $NEEDLIST | sed 's/ \+/\\\n/'`
    if [ -n "$MISSEDPAKAGES" ]; then
      if [ -n "$1" ]; then
        zenity --info --text "`lotext INSTALL_1`:\n\n$MISSEDPAKAGES"
        return 1
      fi
      if zenity --question\
       --text "`lotext INSTALL_2`\n\n$MISSEDPAKAGES"; then
        if [ -z "`printmissing xterm`" ]; then
          MISSEDPAKAGES=$(echo `printmissing $NEEDLIST`)
          xterm -e "echo \"sudo apt-get install $MISSEDPAKAGES\" && \
           sudo apt-get install $MISSEDPAKAGES && exit" 
        else
          zenity --warning --text "`lotext INSTALL_3`"
          fi
      else
        return 1
      fi
    fi
    PACKAGE=`dpkg -l | awk '{ print $2 }'`
    MISSEDPAKAGES=`printmissing $NEEDLIST | sed 's/ \+/\\\n/'`
    if [ -n "$MISSEDPAKAGES" ]; then
      zenity --warning\
       --text "`lotext INSTALL_4`:\n\n$MISSEDPAKAGES"
      return 1
    else
      echo "ok"
    fi
  else
    if [ -n "`printmissing $NEEDLIST`" ]; then
      if [ -n "$1" ]; then
        printmissing $NEEDLIST
        return 1
      fi
      echo "`lotext INSTALL_4`:"
      printmissing $NEEDLIST
      lotext INSTALL_5
      read IANS      
      case "$IANS" in
       yes|y|j|ja|Yes|YES|Ja|JA)         
         MISSEDPAKAGES=$(echo `printmissing $NEEDLIST`)
         echo "sudo apt-get install $MISSEDPAKAGES"
         sudo apt-get install $MISSEDPAKAGES
         ;;        
       *)
         return 1
        ;;
      esac
    fi
    PACKAGE=`dpkg -l | awk '{ print $2 }'`
    if [ -n "`printmissing $NEEDLIST`" ]; then
      return 1
    else
      echo "ok"
    fi
  fi
}
#-----------------------------------------------------------------------------#
#  Anzeige der Hilfe                                                          #
#  Shows Help                                                                 #
#-----------------------------------------------------------------------------#
hilfe(){
  echo "$0 <$ENDUNGAB file> < .. >"
  echo "-h        :  Zeigt diesen Hilfetext an"
  echo "-n        :  Kommandozeilenmodus"
  echo "-r        :  Vorlesen eines eBook(s)"
  echo "-w        :  Weiterlesen eines eBook(s)"
  echo "-l        :  Zeigt eBook(s) mit \"less\" oder \"zenity\" an"
  echo ""
  echo "Folgende Parameter legen den zu benutzenden Standard fest."
  echo "Die Konfigurationsdatei kann auch manuell angepasst werden:"
  echo "siehe: \"$CONFIGFILE\""
  echo ""
  echo "-c, -T    :  Verwenden von cuneiform"
  echo "-t, -C    :  Verwenden von Tesseract (Standard)"
  echo "          :  Tesseract: etwas besser bei reinem Text, langsamer"
  echo "          :  Cuneiform: Besser bei formatiertem Text, schneller"
  echo "-f        :  Filterung von Sonderzeichen (Standard)"
  echo "-F        :  Keine Filterung von Sonderzeichen"
  echo "-s <val>  :  Splitten des Hörbuchs bei <val> 50-600 Sätzen";
  echo "-S        :  Splitten aus";
  echo "-d        :  Doppelsprachige eBooks Verarbeiten (standard)"
  echo "-D        :  Doppelsprachige eBooks nur in Hauptsprache (schneller)" 
  echo "-x        :  auch formatierte txt Datein erzeugen (Standard)";
  echo "-X        :  keine txt Datei erzeugen";
  echo "-v, -M    :  ogg-Vorbis statt mp3 ausgeben erzeugen (Standard)";
  echo "-m, -V    :  mp3 statt ogg-Vorbis ausgeben erzeugen";
  echo "-p        :  Abhängigkeiten prüfen (Standard)";
  echo "-P        :  Abhängigkeiten nicht prüfen";
  echo "          :  (wird ev. für mbrola Sprachpakete"
  echo "          :   unter Ubuntu 9.10 benötigt )";
  echo "-i        :  Abhängigkeiten installieren";
  echo "-I        :  Abhängigkeiten nicht installieren (Standard)";
  echo "-z <char> :  füge Buchsaben zur Liste der lesbaren Buchsaben hinzu";
  echo "-Z        :  Liste der lesbaren Buchsaben auf Standard setzen";  
}
helpmsg(){
  echo "$0 <$ENDUNGAB file> < .. >"
  echo "-h        :  shows this text"
  echo "-n        :  commandline mode"
  echo "-r        :  read eBook(s)"
  echo "-w        :  continue reading eBook(s)"  
  echo "-l        :  shows eBook(s) in \"less\" or \"zenity\""
  echo ""
  echo "following parameter changing the standard configuration."
  echo "if you want to change the configuration manualy:"
  echo "look at: \"$CONFIGFILE\""
  echo ""
  echo "-c, -T    :  use cuneiform"
  echo "-t, -C    :  use tesseract (standard)"
  echo "          :  tesseract is good with pure text but a bit slower"
  echo "          :  cuneiform is good with formated text and faster"
  echo "-f        :  filter text (standard)"
  echo "-F        :  dont filter text "
  echo "-d        :  dual-language eBook handling on (standard)"
  echo "-D        :  dual-language eBook handling off (only 1 lang.)(faster)"  
  echo "-s <val>  :  split audio files at <val> 50-600 lines";
  echo "-S        :  spliting off";
  echo "-x        :  also create formated txt file (standard)";
  echo "-X        :  no txt file";
  echo "-v, -M    :  ogg-Vorbis output (standard)";
  echo "-m, -V    :  mp3 output erzeugen";
  echo "-p        :  check dependencies (standard)";
  echo "-P        :  don't check dependencies";
  echo "          :  (usefull for Ubuntu 9.10 and lower)";
  echo "-i        :  install dependencies";
  echo "-I        :  don't install dependencies (standard)";
  echo "-z <char> :  add char to readable char list";
  echo "-Z        :  set readable char list to standard";  
}
#-----------------------------------------------------------------------------#
#  Parameter Behandlung                                                       #
#  barameter handling                                                         #
#-----------------------------------------------------------------------------#
readparameter() {
while getopts honcCtTfFvVmMs:SpPiIxXdDz:Zrwal opt
do
  case "$opt" in
    h|H)          clear
                  if [ `echo $DEFAULT_LANG | grep lang_deu` ]; then
                    hilfe
                  else
                    helpmsg
                  fi
                  exit;;
    n)            GRAPHIC=;;   
    c|T)          editconf "TES" "";;
    t|C)          editconf "TES" "true";;
    d)            editconf "DUAL_LANG_CHECK" "true";;
    D)            editconf "DUAL_LANG_CHECK" "";;
    f)            editconf "FILTERING" "true";;
    F)            editconf "FILTERING" "";;
    v|M)          editconf "MP3" "";;
    m|V)          editconf "MP3" "true";;
    x)            editconf "CREATE_TEXT_FILE" "true";;
    X)            editconf "CREATE_TEXT_FILE" "";;    
    s)            V_SP="$OPTARG"                  
                  if ( [ -n "$V_SP" ]\
                   && [ $V_SP -le `getconf BORDER_MAX_SPLITTING` ] )
                  then
                    editconf "SPLITTING" "$V_SP"
                  else  
                    echo "-s x | 0=off; x <= `getconf BORDER_MAX_SPLITTING`"
                  fi 2>>"$LOGFILE" ;;
    S)            editconf "SPLITTING" "0";;
    p)            editconf "CHKDEP" "true";;
    P)            editconf "CHKDEP" "";;
    i)            editconf "INDEP" "true";;
    I)            editconf "INDEP" "";;                  
    z)            GRAPHIC=;echo "`getconf XCHAR` --> `getconf XCHAR`$OPTARG"
                  editconf "XCHAR" "`getconf XCHAR`$OPTARG";;
    Z)            editconf "XCHAR" "";;
    r)            TXTAUSWAHL="r";;
    w)            TXTAUSWAHL="w";;
    a)            TXTAUSWAHL="a";;
    l)            TXTAUSWAHL="l";;
    o)            GRAPHIC=;TXTAUSWAHL="o";;
    \?) exit;;
  esac
done
IFS=' '
shift $(($OPTIND - 1))
while [ "$1" ]; do
  echo "$1" >> "$TEMP_DIR/sbooklist.txt"
  shift
done
IFS='
'
}
#-----------------------------------------------------------------------------#
#  Filtern von Textdatei                                                      #
#  filter text file                                                           #
#-----------------------------------------------------------------------------#
filtertext(){
  while read DATEI ; do
    echo "`getoname "$DATEI"`"
    if file "$DATEI" | grep -q ISO-8859 ;then
      iconv -f ISO-8859-1 -t UTF-8 "$DATEI1" > "$TEMP_DIR/ab_filtering.txt"\
      && cp "$TEMP_DIR/ab_filtering.txt" "$DATEI"
    fi
    cp "$DATEI" "$TEMP_DIR/uia.txt"
    cp "$DATEI" "$TEMP_DIR/ab_filtering.txt"
    sed -e 's/\xC2\xA0/ /g;s/\xA0/ /g' "$TEMP_DIR/ab_filtering.txt" |\
    sed '/[^A-Za-z]*\([Pp]age\|Ss]eite\)\+[^A-Za-z]*/d;/^[^A-Za-z]*$/d' |\
    tr '~' ' ' | tr '\n' '~' |\
    sed 's/<?[^>~]*[~]\{,1\}[^~>]*?>//g;s/#\+[^#~]*[~]\{,1\}[^~#]*#\+//g'|\
    sed 's/\[[^~]*[~]\{,1\}[^~]*\.\(jpg\|gif\|png\|tif\)[ ]*\]//g' |\
    sed 's/[\t ]*[\-]\+[\t ]*[~][\t ]*//g;s/[\t ~]\+/ /g' |\
    sed 's/\([A-Za-z][.!?]\)[ ]\+/\1\n/g' |\
    sed '/^[^A-Za-z]*$/d;s/[^A-Za-z 0-9.,!?\-'"$XCHAR"']//g' \
    > "$DATEI"
    echo "."  >> "$DATEI"
    local DATEITO="${DATEI%.*}"
    if [ "`getconf SPLITTING`" == "0" ]; then
      split -l 300 -a 3 "$DATEI" "$DATEITO-"
    else
      if [ `getconf SPLITTING` -le 5 ]; then
        split -l 5 -a 3 "$DATEI" "$DATEITO-"
      else
        split -l `getconf SPLITTING` -a 3 "$DATEI" "$DATEITO-"
      fi
    fi
    local SDATEI
    for SDATEI in "$DATEITO-"*; do
      mv "$SDATEI" "$SDATEI.txt"
      echo "$SDATEI.txt" >> "$TEMP_DIR/fbooklist.txt"        
    done
    rm "$DATEI" 2> "$LOGFILE"
  done < "$1"
}
#-----------------------------------------------------------------------------#
#  Filtern von Textdateiliste für TTS                                         #
#  filter textfile-list for TTS                                               #
#-----------------------------------------------------------------------------#
filter(){
  local DATEI
  >"$TEMP_DIR/fbooklist.txt"
  if [ $GRAPHIC ]; then
    filtertext "$TEMP_DIR/wbooklist.txt"|\
     zenity --progress --pulsate --title "`lotext FILTER_1`"\
      --no-cancel --auto-close
  else
    filtertext "$TEMP_DIR/wbooklist.txt"
    echo -e "$LEISTE"
    echo "`lotext FILTER_1`"
    echo -e "$LEISTE"
  fi
}
###############################################################################
#######################"                           "###########################
######################        Optionen               ##########################
######################         options               ##########################
#######################,                           ,###########################
###############################################################################
optst(){
  echo "$1" >> "$TEMP_DIR/ab_change_options.txt"
  if [ -n "`getconf $1`" ]; then
    echo -n TRUE
  else
    echo -n FALSE
  fi 
}
options(){
  >"$TEMP_DIR/ab_change_options.txt"
  local ABOPT=$(zenity --list --title "abtool - AudioBook Tool" --text "" \
   --checklist\
   --text="`lotext OPTION_1`"\
   --separator="\n"\
   --column="X"\
   --column="SHORT"\
   --column="`lotext OPTION_2`"\
   --column="`lotext OPTION_3`:"\
   --column="`lotext OPTION_4`:"\
   --hide-column=2 \
   --width=640 \
   --height=360 \
   "`optst TES`" "TES"\
    "`lotext OPTION_5`"                            "tesseract"    "cunaiform"\
   "`optst MP3`" "MP3"\
    "`lotext OPTION_6`"                            "mp3"          "ogg"\
   "`optst FILTERING`" "FILTERING"\
    "`lotext OPTION_7`"                 "`lotext SIMPLE_5`" "`lotext SIMPLE_4`"\
   "`optst DUAL_LANG_CHECK`" "DUAL_LANG_CHECK"\
    "`lotext OPTION_8`"               "`lotext OPTION_12`" "`lotext OPTION_13`"\
   "`optst CREATE_TEXT_FILE`" "CREATE_TEXT_FILE"\
    "`lotext OPTION_9`"                 "`lotext SIMPLE_1`" "`lotext SIMPLE_2`"\
   "`optst CHKDEP`"  "CHKDEP"\
    "`lotext OPTION_10`"                "`lotext SIMPLE_1`" "`lotext SIMPLE_2`"\
   "`optst INDEP`" "INDEP"\
    "`lotext OPTION_11`"                "`lotext SIMPLE_3`" "`lotext SIMPLE_4`")
  if [ -n "$ABOPT" ]; then
    while read BB ; do
      if (echo -e "$ABOPT" | grep -q "$BB"); then
        editconf "$BB" "true"
      else
        editconf "$BB" ""
      fi
    done < "$TEMP_DIR/ab_change_options.txt"
  fi
}
###############################################################################
#######################"                           "###########################
######################        Sprachoptionen         ##########################
######################       language options        ##########################
#######################,                           ,###########################
###############################################################################
langoptions(){
    local LANGOPT=$(
    echo "TRUE"
    echo "$CONFIGFILE"
    echo "OUT_TEXT_WIDTH"    
    echo "`lotext SIMPLE_6`"
    echo "`lotext L_OPTION_1`"
    echo "`getconf OUT_TEXT_WIDTH "$CONFILE"`"
    echo "`getconf BORDER_MIN_OUT_TEXT_WIDTH`"
    echo "`getconf BORDER_MAX_OUT_TEXT_WIDTH`"
    echo "FALSE"
    echo "$CONFIGFILE"
    echo "SPLITTING"    
    echo "`lotext SIMPLE_6`"
    echo "`lotext L_OPTION_2`"
    echo "`getconf SPLITTING "$CONFILE"`"
    echo "`getconf BORDER_MIN_SPLITTING`"
    echo "`getconf BORDER_MAX_SPLITTING`"
    for CONFILE in $HOME/.abtool/lang_* ; do
      echo  "FALSE"
      echo  "$CONFILE"
      echo  "MBROLA_SPEED"
      echo  "`getlangconf NAME "$CONFILE"`"
      echo  "`lotext L_OPTION_3`"
      echo  "`getlangconf MBROLA_SPEED "$CONFILE"`"
      echo "`getconf BORDER_MIN_MBROLA_SPEED`"
      echo "`getconf BORDER_MAX_MBROLA_SPEED`"
    done
    for CONFILE in $HOME/.abtool/lang_* ; do
      echo  "FALSE"
      echo  "$CONFILE"
      echo  "MBROLA_PITCH"
      echo  "`getlangconf NAME "$CONFILE"`"
      echo  "`lotext L_OPTION_4`"
      echo  "`getlangconf MBROLA_PITCH "$CONFILE"`"
      echo "`getconf BORDER_MIN_MBROLA_PITCH`"
      echo "`getconf BORDER_MAX_MBROLA_PITCH`"
    done
  )
  local ABOPT=$(zenity --list --title "abtool - AudioBook Tool" --text "" \
   --radiolist\
   --separator="\n"\
   --column="X"\
   --column="FILE"\
   --column="TODO"\
   --column="`lotext L_OPTION_5`"\
   --column="`lotext L_OPTION_6`"\
   --column="`lotext L_OPTION_7`"\
   --column="`lotext L_OPTION_8`"\
   --column="`lotext L_OPTION_9`"\
   --print-column=3,6,2 \
   --hide-column=2,3 \
   --width=700 \
   --height=360 \
  $LANGOPT)  
  local ABNAM=`echo -e "$ABOPT" | sed -n '1p'`
  local ABVAL=`echo -e "$ABOPT" | sed -n '2p'`
  local ABDAT=`echo -e "$ABOPT" | sed -n '3p'`
  if [ -n "$ABOPT" ]; then
    local ABVAL=$(zenity --scale --title="abtool - AudioBook Tool"\
     --value="$ABVAL"\
     --min-value=`getconf BORDER_MIN_$ABNAM`\
     --max-value=`getconf BORDER_MAX_$ABNAM`)
    if [ -n "$ABVAL" ]; then editlangconf "$ABNAM" "$ABVAL" "$ABDAT"; fi
  fi  
}
###############################################################################
#######################"                           "###########################
######################        Dateiauswahl           ##########################
######################       choose file(s)          ##########################
#######################,                           ,###########################
###############################################################################
choose() {
local FALSEFILE=
if [ -f "$TEMP_DIR/sbooklist.txt" ]; then
  while read DATEI ; do
    if [ ! -f "$DATEI" ]; then
      FALSEFILE=true      
      echo -ne "$DATEI\n"      
    fi
  done < "$TEMP_DIR/sbooklist.txt"
  if [ $FALSEFILE ]; then
    if [ $GRAPHIC ]; then  
      local TSOURCE=$(zenity\
       --file-selection\
       --multiple\
       --separator="\n"\
       --file-filter="eBook | $ENDUNGEN"\
       --text="`lotext CHOOSE_1`:"\
       --title "`lotext CHOOSE_2`")
      if [ ! "$TSOURCE" ]; then
        echo "`lotext CHOOSE_3`"
        return 1        
      fi
      echo -e "$TSOURCE" > "$TEMP_DIR/sbooklist.txt"
      return 0
    else
      echo -e "$LEISTE"
      echo "`lotext CHOOSE_3`"
      exit 255
    fi
  fi
else
  if [ $GRAPHIC ]; then  
    local TSOURCE=$(zenity\
     --file-selection\
     --multiple\
     --separator="\n"\
     --file-filter="eBook | $ENDUNGEN"\
     --text="`lotext CHOOSE_4`:"\
     --title "`lotext CHOOSE_2`")
    if [ ! "$TSOURCE" ]; then
      echo "`lotext CHOOSE_3`"
      return 1
    fi
    echo -e "$TSOURCE" > "$TEMP_DIR/sbooklist.txt"
  else  
    echo "`lotext CHOOSE_3`"
    exit 255
  fi
fi
}
###############################################################################
###"                                                                       "###
##"         Source                                                          "##
##            &#9474;                     erweiterte                               ##
#"            &#8595;                    Spracherkennung                           "#
#        Datei-Liste—————&#9488;             &#9474;   &#9474;                                  #
#             &#9474;          &#8595;             &#9474;   &#9474;                                  #
#             &#9474;         Text-Liste&#9472;&#9472;> Splitten  &#9472;&#9472;>  audio-Datei&#9472;&#9472;> txt       #
#             &#8595;          &#8593;                               Liste      Version   #
#,      Bilder-liste—————&#9496;                                 &#9474;                 ,#
##                                                         &#8595;                 ##
##,                                                    audiobook            ,##
###,                                                                       ,###
###############################################################################
###############################################################################
###"                                                                       "###
##"         source                                                          "##
##            &#9474;                      extended                                ##
#"            &#8595;                    language select                           "#
#         file-Liste—————&#9488;             &#9474; &#9474;                                    #
#             &#9474;          &#8595;             &#9474; &#8595;                                    #
#             &#9474;         text-list &#9472;&#9472;> split  —————> audio-file   &#9472;&#9472;> txt      #
#             &#8595;          &#8593;                            list           version  #
#,      picture-list—————&#9496;                               &#9474;                   ,#
##                                                       &#8595;                   ##
##,                                                  audiobook              ,##
###,                                                                       ,###
###############################################################################
#
#
###############################################################################
#######################"                           "###########################
######################    Bild    -> OCR -> Text     ##########################
######################    picture -> OCR -> text     ##########################
#######################,                           ,###########################
###############################################################################
runocr() {    
  >"$TEMP_DIR/sc.txt"
  if [ -z "`getconf TES`" ]; then
    cuneiform -l "`getcurlangconf CUN_OCRLANG`"\
     -f smarttext -o "$TEMP_DIR/sc.txt" "$1"
  else
    if [ `echo "$1" | grep "converted"` ]; then
      tesseract "$1" "$TEMP_DIR/sc" -l "`getcurlangconf TES_OCRLANG`"
    else
      convert -compress none "$1" "$TEMP_DIR/tmp.tif"
      tesseract "$TEMP_DIR/tmp.tif" "$TEMP_DIR/sc"\
       -l "`getcurlangconf TES_OCRLANG`"
    fi
  fi
}
###############################################################################
######################"                             "##########################
#####################     Bilderliste -> txt-liste      #######################
#####################     picture list -> txt-liste      ######################
######################,                             ,##########################
###############################################################################
ocrbook() {
if [ -z "`getconf TES`" ]; then
  local FORMAT=`getconf CUN_FORMAT`
  local ENDUNG=`getconf CUN_END`
  local USEDOCR="Cunaiform "
else
  local FORMAT=`getconf TES_FORMAT`
  local ENDUNG=`getconf TES_END`
  local USEDOCR="Tesseract"
fi
ANZPAGES=`wc -l "$1" | cut -d ' ' -f 1`
PAGENR=1
>"$2"
if [ $GRAPHIC ]; then
  (
  while read PAGE ; do
    echo "# `lotext OCR_1`: $PAGENR / $ANZPAGES\
    \n`lotext OCR_2`: `getcurlangconf NAME`"    
    PROZ=$(( $PAGENR *100 / $ANZPAGES ))
    if [ $PROZ -gt 99 ]; then PROZ=99; fi
    echo "$PROZ"
    runocr "$PAGE" > /dev/null 2>> "$LOGFILE"
    setlang "$TEMP_DIR/sc.txt"
    if [ $CHANGED_LANG ]; then
    echo "# `lotext OCR_1`: $PAGENR / $ANZPAGES\
    \n`lotext OCR_3`: `getcurlangconf NAME`"      
      runocr "$PAGE" > /dev/null 2>> "$LOGFILE"
    fi
    if [ `getconf FILTERING` ]; then
      chkpage "$TEMP_DIR/sc.txt" && cat "$TEMP_DIR/sc.txt" >> "$2"
    else
      cat "$TEMP_DIR/sc.txt" >> "$2" 2>> "$LOGFILE"
    fi
    (( PAGENR++ ))
  done < "$1"
  ) | zenity --progress --text "`lotext OCR_1`: $PAGENR / $ANZPAGES\
      \n`lotext OCR_2`: (`getcurlangconf NAME`)"\
      --title "$USEDOCR"\
      --auto-close --no-cancel\
      --percentage=0 --width 350
else
  echo -n "`lotext OCR_1`:     "
  while read PAGE ; do
    PROZ="    $(( $PAGENR * 100 / $ANZPAGES ))"
    echo -ne "\010\010\010\010"
    echo -ne "${PROZ:(-3)}%"
    runocr "$PAGE" > /dev/null 2>> "$LOGFILE"
    setlang "$TEMP_DIR/sc.txt" > /dev/null 
    if [ $CHANGED_LANG ]; then
      runocr "$PAGE" > /dev/null 2>> "$LOGFILE"
    fi
    if [ `getconf FILTERING` ]; then
      chkpage "$TEMP_DIR/sc.txt" && cat "$TEMP_DIR/sc.txt" >>"$2" 2>>"$LOGFILE"
    else
      cat "$TEMP_DIR/sc.txt" >> "$2" 2>> "$LOGFILE"
    fi    
    (( PAGENR++ ))
  done < "$1"
  echo -e ""
  echo -e "$LEISTE"
fi
rm "$1" 2> /dev/null
}
###############################################################################
###################"                                "##########################
##################     djvu -> Bilderliste            #########################
##################     djvu -> picture list           #########################
###################,                                ,##########################
###############################################################################
djvutool() {
  PAGE="$1"
  TIMEST="$4"
  if [ ! -d "$TEMP_DIR/pic$4" ]; then
    mkdir "$TEMP_DIR/pic$4"
  fi
  ANZPAGES=`djvused "$PAGE" -e 'n'`
  if [ -z "`getconf TES`" ]; then
    FORMAT=`getconf CUN_FORMAT`
    ENDUNG=`getconf CUN_END`
  else
    FORMAT=`getconf TES_FORMAT`
    ENDUNG=`getconf TES_END`
  fi
  if [ $GRAPHIC ]; then
    (
    for DJVUPAGE in `seq 1 $ANZPAGES`; do
      PROZ=$(( $DJVUPAGE * 100 / $ANZPAGES ))
      if [ $PROZ -gt 99 ]; then PROZ=99; fi
      echo "$PROZ"
      echo "# `lotext DJVU_1`: $DJVUPAGE / $ANZPAGES"
      ddjvu -page="$DJVUPAGE" -format="$FORMAT" "$PAGE"\
       "$TEMP_DIR/pic$4/$TIMEST-converted-$3$DJVUPAGE.$ENDUNG"
      echo "$TEMP_DIR/pic$4/$TIMEST-converted-$3$DJVUPAGE.$ENDUNG" >> "$2"
    done
    ) | zenity --progress --text "`lotext DJVU_1`: 1 / $ANZPAGES"\
     --title "$3" --percentage=0 --auto-close --width 350
  else
    echo -n "`lotext DJVU_2`: $3      "
    for DJVUPAGE in `seq 1 $ANZPAGES`; do
      PROZ="   $(( $DJVUPAGE * 100 / $ANZPAGES ))"
      echo -ne "\010\010\010\010"
      echo -ne "${PROZ:(-3)}%"
      ddjvu -page="$DJVUPAGE" -format="$FORMAT" "$PAGE"\
       "$TEMP_DIR/pic$4/$TIMEST-converted-$3$DJVUPAGE.$ENDUNG"
      echo "$TEMP_DIR/pic$4/$TIMEST-converted-$3$DJVUPAGE.$ENDUNG" >> "$2"
    done
    echo -e ""
    echo -e "$LEISTE"
  fi
}
###############################################################################
####################"                                   "######################
###################     Bilder   -> Bilder Liste          #####################
###################     pictures -> picture list          #####################
####################,                                  ,#######################
###############################################################################
conpicture(){
local CNTSOURCE=10000000
local PICS=$(echo "`getconf SINGLE_PIC_FORMAT`$" | sed 's/ /$\\|/g')
cat "$TEMP_DIR/sbooklist.txt" |\
 grep "$PICS" | tr -d '[0-9]' | uniq -d > "$TEMP_DIR/ubooklist.txt"
while read UDATEI ; do
  >"$TEMP_DIR/gbooklist.txt"
  while read DATEI ; do
    local UNIQNAME=`echo $DATEI | tr -d '[0-9]'`
    if [ "$UNIQNAME" == "$UDATEI" ]; then
      if ! grep -q "$TEMP_DIR/${UNIQNAME##*/}-abpic-$CNTSOURCE.abpiclist"\
       "$TEMP_DIR/gbooklist.txt" ; then
        echo "$TEMP_DIR/${UNIQNAME##*/}-abpic-$CNTSOURCE.abpiclist"\
         >> "$TEMP_DIR/gbooklist.txt"
      fi
      echo "$DATEI" >> "$TEMP_DIR/${UNIQNAME##*/}-abpic-$CNTSOURCE.abpiclist"
    else
      if ! grep -q "$DATEI" "$TEMP_DIR/gbooklist.txt" ; then
        echo "$DATEI" >> "$TEMP_DIR/gbooklist.txt"
      fi
    fi
  done < "$TEMP_DIR/sbooklist.txt"
  (( CNTSOURCE++ ))
  mv "$TEMP_DIR/gbooklist.txt" "$TEMP_DIR/sbooklist.txt"
done < "$TEMP_DIR/ubooklist.txt"
>"$TEMP_DIR/gbooklist.txt"
while read DATEI ; do
  if echo "$DATEI" | grep -q "$PICS"; then
    echo "$DATEI" > "$TEMP_DIR/${DATEI##*/}-abpic-$CNTSOURCE.abpiclist"
    echo "$TEMP_DIR/${DATEI##*/}-abpic-$CNTSOURCE.abpiclist"\
     >> "$TEMP_DIR/gbooklist.txt"
    (( CNTSOURCE++ ))
  else
    echo "$DATEI" >> "$TEMP_DIR/gbooklist.txt"
  fi  
done < "$TEMP_DIR/sbooklist.txt"
mv "$TEMP_DIR/gbooklist.txt" "$TEMP_DIR/sbooklist.txt"
}
###############################################################################
####################"                                   "######################
###################     eBook / Bilder   -> Text Liste    #####################
###################     eBook / pictures -> text list     #####################
####################,                                  ,#######################
###############################################################################
work() {
local CNTSOURCE=10000000
conpicture
while read DATEI ; do
  (( CNTSOURCE++ ))
  if [ -f "$DATEI" ]; then
    local ENDOFF=${DATEI##*.}  
    local ENDOFFLOW=$( echo "$ENDOFF" | tr "'[:upper:]'" "'[:lower:]'" )
    local DIROF="$(cd "$(dirname "$DATEI")"; pwd)"
    local NAMEOF=$( basename "$DATEI" | sed 's/\.[^\.]\+$//g' )
    DATEI="`echo "$DIROF/$NAMEOF.$ENDOFF"`"
    if [ ! -f "$DATEI" ]; then
      echo "`lotext SIMPLE_7`"
    else
      local BOOKNAME="$TEMP_DIR/$CNTSOURCE-aBook-$NAMEOF.txt"
      case $ENDOFFLOW in
       pdf)
         pdftotext -enc "UTF-8" -nopgbrk "$DATEI" "$BOOKNAME" 2>> "$LOGFILE";;
       lit)
         mkdir "$TEMP_DIR/$CNTSOURCE-HTML"
         **** -d "$DATEI" "$TEMP_DIR/$CNTSOURCE-HTML" 2>> "$LOGFILE"    
         html2text -utf8 "$TEMP_DIR/$CNTSOURCE-HTML/"*.htm* \
          > "$BOOKNAME" 2>> "$LOGFILE";;
       txt)
         cp "$DATEI" "$TEMP_DIR/$CNTSOURCE-aBook-$NAMEOF.txt";;
       htm|html)
         html2text -utf8 "$DATEI" > "$BOOKNAME" 2>> "$LOGFILE";;
       rtf|doc)
         catdoc "$DATEI" > "$BOOKNAME" 2>> "$LOGFILE";;
       epub)
         mkdir "$TEMP_DIR/$CNTSOURCE-HTML"
         unzip -qq -j "$DATEI" -d "$TEMP_DIR/$CNTSOURCE-HTML"
         html2text -utf8 "$TEMP_DIR/$CNTSOURCE-HTML/"*.htm* \
          > "$BOOKNAME" 2>> "$LOGFILE"
         ;;         
       djvu)         
         djvutool "$DATEI" "$TEMP_DIR/picbooklist" "$NAMEOF" "$CNTSOURCE"
         ocrbook "$TEMP_DIR/picbooklist" "$BOOKNAME";;
       abpiclist)
         DIROF="$(cd "$(dirname `cat $DATEI | head -n 1`)"; pwd)"
         ocrbook "$DATEI" "$BOOKNAME"
         NAMEOF="${NAMEOF%-abpic-*}";;
       *) echo "$ENDOFFLOW - `lotext SIMPLE_7`";exit 1;;
      esac
      echo -e "$BOOKNAME" >> "$TEMP_DIR/wbooklist.txt"
      echo -e "$DIROF" >> "$TEMP_DIR/ordirlist.txt"
      echo -e "$NAMEOF" >> "$TEMP_DIR/ornamelist.txt"
    fi
  fi
done < "$TEMP_DIR/sbooklist.txt"
}
###############################################################################
###############"                                            "##################
##############  formatieren einer Liste unform. Textdateien   #################
##############      format <- unfomatet Textfile-list         #################
###############,                                            ,##################
###############################################################################
formatab(){
  local BOOKFIN
  local DATEI
  while read DATEI ; do
    if [ -f "$DATEI" ]; then
      BOOKFIN="$DATEI"
    else
      BOOKFIN="${DATEI%.*}-absplit-"
    fi
    for DATE in "$BOOKFIN"*; do
      local BOOKDIR="`getdir "$DATE"`"
      local BOOKNAME="`getoname "$DATE"`"
      if [ `getconf CREATE_TEXT_FILE` ]; then
        fmt -w `getconf OUT_TEXT_WIDTH` "$DATE"\
         >> "$BOOKDIR/aBook-$BOOKNAME/$BOOKNAME.txt"
      fi
    done
  done < "$TEMP_DIR/fbooklist.txt"
}
###############################################################################
######################"                             "##########################
#####################    txt-file-Liste -> Hörbuch    #########################
#####################    txt-file-list -> AudioBook   #########################
######################,                             ,##########################
###############################################################################
#
#
#-----------------------------------------------------------------------------#
#  Anzeige des Vortschrittbalkens                                             #
#  Progressbar                                                                #
#-----------------------------------------------------------------------------#
prgbar(){
#starten nach Begin der Umwandlung
  local PROZ=$(( $1 * 100 / $2 ))
  if [ $GRAPHIC ]; then
    if [ $PROZ -gt 99 ]; then PROZ=99; fi
    echo "$PROZ" 1>&2
    echo "# $1 von $2" 1>&2
  #Text Fortschrittsbalken
  else    
    echo -ne "\010\010\010\010\010\010\010\010" 1>&2
    echo -ne "$1 /$2" 1>&2
  fi
}
#-----------------------------------------------------------------------------#
#  Sprachdateien Vereinigen zu einer audiodatei                               #
#  text splitted in languages to one audio file                               #
#-----------------------------------------------------------------------------#
unify(){  
  local BOOKFIN
  local BOOKLINE=1
  if [ -f "$1" ]; then
    BOOKFIN="$1"
  else
    BOOKFIN="${1%.*}-absplit-"
  fi
  for DATE in "$BOOKFIN"*; do
    ENCLINENR=1
    setlang "$DATE" > /dev/null 2>> "$LOGFILE"
    local MB_S="`getcurlangconf MBROLA_SPEED`"
    local MB_V="`getcurlangconf MBROLA_LANG`"
    local MB_P="`getcurlangconf MBROLA_PITCH`"
    local ANZZ=`wc -l "$DATE" | cut -d ' ' -f 1` 2>> "$LOGFILE" 
    if [ -z "`getconf MP3`" ]; then 
      espeak --stdout -f "$DATE" -s $MB_S -v $MB_V -p $MB_P 2>> "$LOGFILE" |\
      oggenc -t "$2" -a Hoerbuch -Q -q 3 - 2>> "$LOGFILE"
    else
      espeak --stdout -f "$DATE" -s $MB_S -v $MB_V -p $MB_P 2>> "$LOGFILE"|\
      lame -q 5 --tt "$2" --ta Hoerbuch -b 16 -h -V 2 -S - 2>> "$LOGFILE"
    fi
  done
}
#-----------------------------------------------------------------------------#
#  mehrere Bücher in mehrere Audio Dateien                                    #
#  Control of changin multiple files into multiple audio files                #
#-----------------------------------------------------------------------------#
makeaudiobook(){
  local DATEI
  local INCVAR=0
  local AINCVAR=1000
  local ANZDAT="      `wc -l "$TEMP_DIR/fbooklist.txt" | cut -d ' ' -f 1`"
  if [ ! $GRAPHIC ]; then
    echo -e "$LEISTE"
    echo -ne "`lotext ABOOK_1`:          "
  fi
  while read DATEI ; do
    (( INCVAR++ ))
    local FINCVAR="    $INCVAR"    
    local BOOKDIROF="`getdir "$DATEI"`"
    local ODIR="`getoname "$DATEI"`" 
    if [ -f "$DATEI" ]; then
      local ORGDATEI="$DATEI"
    else
      local ORGDATEI="$DATEI.del"
    fi
    if [ -n "`getconf MP3`" ]; then
      local THEEND="mp3"
    else
      local THEEND="ogg"
    fi
    if [ ! -d "$BOOKDIROF/aBook-$ODIR" ]; then
      mkdir "$BOOKDIROF/aBook-$ODIR" 2>> "$LOGFILE"
    fi
    local NRSIZE="`ls "$TEMP_DIR"/*.txt | wc -l`"
    NRSIZE=${#NRSIZE}
    AINCVAR="00000000$INCVAR"    
    if [ "`getconf SPLITTING`" == "0" ]; then
      local BOOKNAME="`getoname "$DATEI"`"
    else
      local BOOKNAME="`getoname "$DATEI"`-${AINCVAR:(-$NRSIZE)}"
    fi
    if [ $ANZDAT -gt 0 ]; then
      local PROZ=$(( $INCVAR * 100 / $ANZDAT ))
    else
      local PROZ=99
    fi
    if [ $GRAPHIC ]; then
      if [ $PROZ -gt 99 ]; then PROZ=99; fi
      echo "$PROZ"
      echo "# `lotext ABOOK_1`: ${FINCVAR:(-4)} von ${ANZDAT:(-4)}"
      unify "$DATEI" "$BOOKNAME" \
       >> "$BOOKDIROF/aBook-$ODIR/$BOOKNAME.$THEEND"
    else
      echo -ne "\010\010\010\010\010\010\010\010\010\010"
      echo -ne "${FINCVAR:(-4)} /${ANZDAT:(-4)}"
      unify "$DATEI" "$BOOKNAME"  \
       >> "$BOOKDIROF/aBook-$ODIR/$BOOKNAME.$THEEND"
    fi
  done < "$TEMP_DIR/fbooklist.txt"
  echo  ""
}
makeaudio(){
  if [ $GRAPHIC ]; then
    makeaudiobook | zenity --progress\
     --text="..."\
     --title "abtool - AudioBook"\
     --percentage=0 --width 350 --auto-close
  else
    makeaudiobook
  fi
}
###############################################################################
############"                                                 "################
###########                Vorlesen von Büchern                 ###############
###########                  read books aloud                   ###############
############,                                                 ,################
###############################################################################
#
#
###########^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^###############
###########     Buchliste / Seitennummer -> Vorlesen ab Seite   ###############
###########     list of books / pagenbr -> Read from Page       ###############
###########_____________________________________________________###############
savebook() {
  local DATEI
  local DATE
  local BOOKFIN
  if [ ! -d "$LBOOKDIR" ]; then
    mkdir "$LBOOKDIR"
  fi
  if [ -z "$1" ]; then
    editconf "LASTPOS" "1"
    rm -r "$LBOOKDIR"/* 2> /dev/null
    while read DATEI ; do
      if [ -f "$DATEI" ]; then
        BOOKFIN="$DATEI"
        cp "$BOOKFIN" "$BOOKFIN.tmp" 
        cat "$BOOKFIN.tmp" | tr ' ' '_' | tr '\n' ' ' | fmt -w 400 |\
         tr '_' ' ' > "$BOOKFIN"
         rm "$BOOKFIN.tmp" 2> /dev/null
        cp "$BOOKFIN" "$LBOOKDIR"
      else
        BOOKFIN="${DATEI%.*}-absplit-"
        for DATE in "$BOOKFIN"*; do
          cp "$DATE" "$DATE.tmp" 
          cat "$DATE.tmp" | tr ' ' '_' | tr '\n' ' ' | fmt -w 400 |\
           tr '_' ' ' > "$DATE"
          rm "$DATE.tmp" 2> /dev/null
        done        
        cp "$BOOKFIN"* "$LBOOKDIR"
      fi
    done < "$TEMP_DIR/fbooklist.txt"
    ls "$LBOOKDIR"/* >> "$LBOOKDIR/lbooklist"
  fi
}
###########^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^###############
###########     Buchliste / Seitennummer -> Vorlesen ab Seite   ###############
###########     list of books / pagenbr -> Read from Page       ###############
###########_____________________________________________________###############
readbook() {
  savebook "$1"
  local DATEI
  local PAGENBR
  local PAGE=1
  local AGAIN=false  
  local SENTENCE  
  local ANZ_RDB_WRD="`cat "$LBOOKDIR"/*.txt | wc -l`"
  local PSELECT=true
  while true; do
    editconf "LASTBOOK" "true"
    PAGENBR="`getconf "LASTPOS"`"
    if [ $GRAPHIC ]; then
      if [ $ANZ_RDB_WRD -le 1 ]; then (( ANZ_RDB_WRD++ )); fi
      if $AGAIN ; then
        PAGENBR=$(zenity --scale --text "`lotext READBOOK_1`"\
         --min-value=1 --max-value=$ANZ_RDB_WRD --title "`lotext READBOOK_2`"\
         --value="`getconf "LASTPOS"`")
        rm "$LBOOKDIR/reading" 2> "$LOGFILE"
        while [ ! -f "$LBOOKDIR/exit" ]; do
          sleep 2
        done        
        rm "$LBOOKDIR/exit" 2> "$LOGFILE"
        if [ $PAGENBR ]; then
          editconf "LASTPOS" "$PAGENBR"
          touch "$LBOOKDIR/reading"
        else
          rm "$LBOOKDIR/reading" 2> "$LOGFILE"
          if [ -n "$TXTAUSWAHL" ]; then
            exit
          else
            break
          fi
        fi
      else
        touch "$LBOOKDIR/reading"
        AGAIN=true
      fi
    fi
    local SENNR=1  
    if [ $GRAPHIC ]; then 
      while read DATEI ; do
        setlang "$DATEI" > /dev/null
        while read SENTENCE; do
          if [ $PAGE -ge $PAGENBR ]; then
            echo "#  `echo -e "$SENTENCE\n\n\n\n\n\n" | fmt -w 80 |\
            sed -e 's/$/\\\n/g' |head -n 6 |tr '\n' ' '`\n$PAGE / $ANZ_RDB_WRD"
            echo "$(( $PAGE * 100 / $ANZ_RDB_WRD ))"
            editconf "LASTPOS" "$PAGE"            
            espeak -p `getcurlangconf MBROLA_PITCH`\
             -s `getcurlangconf MBROLA_SPEED`\
             -v `getcurlangconf MBROLA_LANG` "$SENTENCE"\
              2>> "$LOGFILE" > /dev/null
            if [ ! -f "$LBOOKDIR/reading" ]; then
              touch "$LBOOKDIR/exit"
              exit
            fi   
          fi
          (( PAGE++ ))        
        done < "$DATEI"
        SENNR=1
      done < "$LBOOKDIR/lbooklist" |\
       zenity --progress --title "`lotext READBOOK_3`" \
       --height 250 --width 580  --auto-close --no-cancel 2> "$LOGFILE" &     
       #--cancel-label "`lotext READBOOK_4`" --auto-kill
    else
      while read DATEI ; do
        setlang "$DATEI" > /dev/null
        while read SENTENCE; do            
          if [ $PAGE -ge $PAGENBR ]; then            
            clear
            echo "--------------------------------------------------"
            echo "$SENTENCE" | fmt -w 50
            echo "--------------------------------------------------"
            echo -n "$(( $PAGE * 100 / $ANZ_RDB_WRD ))%  "
            echo -n "Stop: ctrl-c, Resume: $0 -w"  
            espeak -p `getcurlangconf MBROLA_PITCH`\
             -s `getcurlangconf MBROLA_SPEED`\
             -v `getcurlangconf MBROLA_LANG` "$SENTENCE"\
              2>> "$LOGFILE" > /dev/null
              editconf "LASTPOS" "$PAGE"
          fi
          (( PAGE++ ))
        done < "$DATEI"
        SENNR=1
      done < "$LBOOKDIR/lbooklist"
      echo ""
      echo "The End"
      exit 255
    fi
  done
}
###########^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^###############
###########     Buchliste / Seitennummer -> Vorlesen ab Seite   ###############
###########     list of books / pagenbr -> Read from Page       ###############
###########_____________________________________________________###############
showbook(){
  while read DATEI ; do
    if [ -f "$DATEI" ]; then
      BOOKFIN="$DATEI"
    else
      BOOKFIN="${DATEI%.*}-absplit-"
    fi
    for DATE in "$BOOKFIN"*; do
      fmt -w 79 "$DATE" >> "$TEMP_DIR/zusammen.txt"
    done
  done < "$TEMP_DIR/fbooklist.txt"
  if [ $GRAPHIC ]; then 
    zenity --text-info --width 650 --height 800\
     --filename "$TEMP_DIR/zusammen.txt" 2> "$LOGFILE"
    BNAME=$( zenity --entry --text "`lotext READBOOK_5`"\
     --title "`lotext READBOOK_6`" | sed 's/\.txt//g')
  else
    less "$TEMP_DIR/zusammen.txt"
    clear
    echo "`lotext READBOOK_7`"
    read BNAME
  fi
  if [ -n "$BNAME" ]; then            
    cp "$TEMP_DIR/zusammen.txt" "$HOME/aBook-$BNAME.txt"         
  fi
}
###############################################################################
#######################"                           "###########################
######################          Hauptmenu            ##########################
######################          main-menu            ##########################
#######################,                           ,###########################
###############################################################################
BEENDEN=
rm -r "$TEMP_DIR"/* 2> /dev/null
readparameter $*
setxchar
if [ ! $GRAPHIC ]; then clear;echo -e "$LEISTE"; fi 
if [ -n "`getconf CHKDEP`" ]; then
  if [ ! $GRAPHIC ]; then echo -ne "`lotext INSTALL_7`: "; fi
  if [ -n "`getconf INDEP`" ]; then
    if ! instdep ; then
      echo "`lotext INSTALL_6`" 1>&2
      exit 255
    fi
  else
    if ! instdep "check" ; then
      echo "`lotext INSTALL_6`" 1>&2
      exit 255
    fi    
  fi
  if [ ! $GRAPHIC ]; then echo -e "$LEISTE"; fi
fi
#-----------------------------------------------------------------------------#
#  Parametermodus mit nachfolgenden Text / Dateien                            #
#  parameter mode with following text or files                                #
#-----------------------------------------------------------------------------#
if [ -f "$TEMP_DIR/sbooklist.txt" ]; then
  case "$TXTAUSWAHL" in
   l)
    choose
    work
    filter
    showbook
    ;;
   r)
    choose
    work
    filter
    duallang
    readbook
    ;;
   w) 
    exit 1;;
   a)
    cat "$TEMP_DIR/sbooklist.txt" | tr '\n' ' ' > "$TEMP_DIR/saybook.txt"
    echo "$TEMP_DIR/saybook.txt" > "$TEMP_DIR/sbooklist.txt"
    work
    filter
    duallang
    readbook
    ;;
   *)
    choose
    work
    filter
    duallang
    makeaudio
    formatab
    ;;
  esac
  BEENDEN=true
#-----------------------------------------------------------------------------#
#  Parametermodus ohne nachfolgenden Text / Dateien                           #
#  parameter mode without following text or files                             #
#-----------------------------------------------------------------------------#
else
  case "$TXTAUSWAHL" in
   a)
    if [ ! $GRAPHIC ]; then
      echo "`lotext MENU_1`:"
      read WTEXT
    else
      WTEXT=$(zenity --text-info --editable --title "abtool")
    fi
    echo "$WTEXT" | tr '\n' ' ' > "$TEMP_DIR/saybook.txt"
    echo "$TEMP_DIR/saybook.txt" > "$TEMP_DIR/sbooklist.txt"
    work
    filter
    duallang
    readbook
    ;;
   o) 
    changedefaultlang
    ;;    
   w) 
    readbook "`getconf "LASTPOS"`"
    ;;
   *)
    if [ ! $GRAPHIC ]; then
      BEENDEN=true
    fi
    ;;
  esac
fi
while [ ! $BEENDEN ]; do
  HILFETEXT="`getlangconf MBROLA_HELP "$DEFAULT_LANG"`"
  TXTAUSWAHL=
  if [ -z "`getconf "LASTBOOK"`" ]; then
    LASTONE=""
  else
    LASTONE="`lotext MENU_2`"
  fi
  if [ $GRAPHIC ]; then
    AUSWAHL=$(zenity --list --title "abtool - AudioBook Tool" --text "" \
     --cancel-label="`lotext MENU_10`"\
     --column=Auswahl --hide-header \
     --width=200 \
     --height=320 \
     "`lotext MENU_3`" \
     "`lotext MENU_4`" \
     $LASTONE \
     "`lotext MENU_5`" \
     "`lotext MENU_6`" \
     "`lotext MENU_7`"\
     "`lotext MENU_8`")
  fi
  case "$AUSWAHL" in
   #create
   "`lotext MENU_3`")
     if choose ; then
       work
       filter
       duallang
       makeaudio
       formatab
     fi
     ;;
#  read        
   "`lotext MENU_4`")          
     if choose ; then
       work
       filter
       duallang
       readbook
     fi
     ;;
#  continue
   "`lotext MENU_2`")
     readbook "`getconf "LASTPOS"`"
     ;;
#  view
   "`lotext MENU_5`")
     if choose ; then
       work
       filter
       showbook
     fi
     ;;
#  help
   "`lotext MENU_6`")     
     (espeak -p `getlangconf MBROLA_PITCH "$DEFAULT_LANG"`\
      -s `getlangconf MBROLA_SPEED "$DEFAULT_LANG"`\
      -v `getlangconf MBROLA_LANG "$DEFAULT_LANG"`\
      "$HILFETEXT" 2>> "$LOGFILE") |\
       zenity  --info --text "`echo "$HILFETEXT" | sed 's/[0-9]\+[.]/\n&/g'`" &
      ;;
#   settings
    "`lotext MENU_8`")
     options
     changedefaultlang
     ;;
#    lang settings
     "`lotext MENU_7`")
     langoptions
     ;;
   *) BEENDEN=true;;
  esac
  AUSWAHL=""
rm -r "$TEMP_DIR"/* 2> /dev/null
done
if [ ! $GRAPHIC ]; then
  echo -e "$LEISTE"
  echo "`lotext MENU_9`"
fi
exit

```

---

### Post by frytek on 2011-07-18
A very nice job. Some people will never find it 'normal' to listen to audiobooks created with speech synthesis but that is also what I like and do. 

I just want to say that after my first fascination with "espeak + mbrola" I came back just to espeak. I realized I can understand it better and I can play the files faster (I mean: I make them with a greater words per minute ratio). Most people would say that espeak sounds like robots in old sf movies but the speech is definitely more clear. 

:)

The script that I found somewhere is much simpler but it uses some sox effects. Perhaps you'd be interested: 
```

#!/bin/sh
# txt2mp3 - convert text files to mp3 audio files (aka audiobooks)
# v0.1
#
# (c) 2008 Everthon Valadão <everthonvaladao@gmail.com> under the GPL
#          http://www.gnu.org/copyleft/gpl.html
#
# OBS.: install some pre-requisites first, with
#       sudo apt-get install espeak lame xpdf-utils odt2txt antiword

TXT_FILE="$1"
BASENAME=`echo "$TXT_FILE" | sed 's/\(.*\)\(\....$\)/\1/g'`

echo "TTS (text-to-speach) ${TXT_FILE}"


#encode=comment_to_listen_instead_of_encoding

# espeak parameters
# mbrola voice is defaulting to british.
speed=180	#160
paragraph=40	#0
pitch=50	#50



# sox effects 
soxeffect_book="vol 0.7 pad 0 0.2  vol 1 amplitude 0.05 contrast 30"
#soxeffect_book="vol 0.7 pad 0 0.2 reverb 40 40 10 vol 2.5 amplitude 0.05 contrast"
# lame parameters
lame_mode=m
bitrate=32



#s: speed words per minute default 170, a: amplitude
# espeak write output to a pipe while lame encodes the file on the fly
espeak -s $speed -a 10 -l $paragraph -p $pitch -v mb-en1  -f "$1" | \
mbrola -e -v 1.2 /usr/share/mbrola/voices/en1 - - | (
if [ -n "$encode" ] ; then
	sox -s -c 1 -r 16000 -t raw -2 - -s  -r 16000 -2 -t raw -c 1 - $soxeffect_book | \
	lame -r $endian -s 16 -b$bitrate -m $lame_mode - "${BASENAME}_espeak.mp3"
else
	aplay -r16000 -fS16
fi
	)


#echo "...done! Voice saved as ${1}_espeak-mbr.mp3"


```

---

