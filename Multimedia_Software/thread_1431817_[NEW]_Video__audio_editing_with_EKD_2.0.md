---
title: "[NEW] Video / audio editing with EKD 2.0"
date: 2010-03-17
forum: Multimedia Software
---

### Post by YannBuntu on 2010-03-17
EDIT: software has been updated, please see messages below.



-----------------------
Release of EKD 2.0 

- _[Screenshots. ]("http://ekd.tuxfamily.org/index.php/CopiesEcran/Anglais")_
- _Installation instructions :_

1) Add the following repository in menu System->Administration->Software sources (change "karmic" by your Ubuntu version): ```
deb http://download.tuxfamily.org/ekdforum/ekd karmic contrib
```
2) Add the key (optional) in a terminal: ```
wget http://download.tuxfamily.org/ekdforum/ekd/cle-ekd.key.asc -O - | sudo apt-key add -
```
3) Reload your list of packages
4) Install the package "ekd"

---

### Post by wmstrome on 2012-01-13
> **YannBuntu said:**
> Release of EKD 2.0 

- _[Screenshots. ]("http://ekd.tuxfamily.org/index.php/CopiesEcran/Anglais")_
- _Installation instructions :_

1) Add the following repository in menu System->Administration->Software sources (change "karmic" by your Ubuntu version): ```
deb http://download.tuxfamily.org/ekdforum/ekd karmic contrib
```
2) Add the key (optional) in a terminal: ```
wget http://download.tuxfamily.org/ekdforum/ekd/cle-ekd.key.asc -O - | sudo apt-key add -
```
3) Reload your list of packages
4) Install the package "ekd"
I tried this (substituting natty for karmic) and got the following error in synaptic:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.tuxfamily.org/ekdforum/ekd/dists/natty/Release](http://download.tuxfamily.org/ekdforum/ekd/dists/natty/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

---

### Post by YannBuntu on 2012-01-13
Wow, an answer after 2 years ! ;)

Please look at the official EKD website : [http://ekd.tuxfamily.org/index.php/Accueil/AccueilEnglish](http://ekd.tuxfamily.org/index.php/Accueil/AccueilEnglish)

---

### Post by monsitt on 2012-01-14
> **wmstrome said:**
> I tried this (substituting natty for karmic) and got the following error in synaptic:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.tuxfamily.org/ekdforum/ekd/dists/natty/Release](http://download.tuxfamily.org/ekdforum/ekd/dists/natty/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

Hello :D,

I'm the historical developper of EKD (EnKoDeur-Mixeur). **EKD is now in version 3.0.1**, if you want to know what EKD can do for you, you will see here:

[http://ekd.tuxfamily.org/index.php/Presentation/LinuxEnglish](http://ekd.tuxfamily.org/index.php/Presentation/LinuxEnglish)

Here are some new features listed here (only in french, sorry):

[http://codingteam.net/project/ekd/news/show/496-changements_de_la_version_201_e_la_version_actuelle_210](http://codingteam.net/project/ekd/news/show/496-changements_de_la_version_201_e_la_version_actuelle_210)

You can install by the EKD reposity ...

**1) Edit your [COLOR=Red]/[/COLOR][COLOR=red][B]etc/apt/sources.list [COLOR=Black]like that:[/COLOR]**[/COLOR][/B]

```
**## EKD (EnKoDeur-Mixeur)** 
**deb http://download.tuxfamily.org/ekdforum/ekd [COLOR=red]xxxx[/COLOR] contrib**
```[B]

ATTENTION [COLOR=Red]xxxx[/COLOR] should be replaced by your version of Debian or Ubuntu (ie for Debian:**[COLOR=red] etch[/COLOR], [COLOR=red]lenny[/COLOR], [COLOR=red]squeeze[/COLOR], [COLOR=red]wheezy[/COLOR] or [COLOR=red]sid[/COLOR], and for Ubuntu: [COLOR=red]dapper[/COLOR], [COLOR=red]edgy[/COLOR], [COLOR=red]feisty[/COLOR], [COLOR=red]gutsy[/COLOR], [COLOR=red]hardy[/COLOR], [COLOR=red]intrepid[/COLOR], [COLOR=red]jaunty[/COLOR], [COLOR=red]karmic[/COLOR], [COLOR=red]lucid[/COLOR], [COLOR=red]maverick[/COLOR], [COLOR=red]natty[/COLOR], [COLOR=red]oneiric[/COLOR] or [COLOR=red]precise-pangolin[/COLOR]**[/B]

**2) Add the encryption key (for Ubuntu):**

```
[COLOR=red]**wget http://download.tuxfamily.org/ekdforum/ekd/cle-ekd.key.asc -O - | sudo apt-key add -**[/COLOR]
```**3) Since the latest version EKD uses G'MIC as a dependency ; e****dit your [COLOR=Red]/[/COLOR][COLOR=red][B]etc/apt/sources.list [COLOR=Black]like that:[/COLOR]**[/COLOR][/B]

```
## apt reposity for G&#8217;MIC
deb http://download.tuxfamily.org/ekdforum/ekd/gmic/gmic_apt xxxx contrib
```** ATTENTION [COLOR=Red]xxxx[/COLOR] should be replaced by your version of Debian or Ubuntu (ie for Debian:[B][COLOR=red] etch[/COLOR], [COLOR=red]lenny[/COLOR], [COLOR=red]squeeze[/COLOR], [COLOR=red]wheezy[/COLOR] or [COLOR=red]sid[/COLOR], and for Ubuntu: [COLOR=red]dapper[/COLOR], [COLOR=red]edgy[/COLOR], [COLOR=red]feisty[/COLOR], [COLOR=red]gutsy[/COLOR], [COLOR=red]hardy[/COLOR], [COLOR=red]intrepid[/COLOR], [COLOR=red]jaunty[/COLOR], [COLOR=red]karmic[/COLOR], [COLOR=red]lucid[/COLOR], [COLOR=red]maverick[/COLOR], [COLOR=red]natty[/COLOR], [COLOR=red]oneiric[/COLOR] or [COLOR=red]precise-pangolin[/COLOR]**[/B]

**4) Refresh of your sources.list:**

```
**sudo apt-get update**
```[B]

5) Installation of G'MIC and EKD:[/B]

```
**sudo apt-get install gmic ekd**
```

If you want you can see that in french here:

[http://ekd.tuxfamily.org/index.php/INSTekd/LinuxDepotDebUbuntu](http://ekd.tuxfamily.org/index.php/INSTekd/LinuxDepotDebUbuntu)

[http://ekd.tuxfamily.org/index.php/INSTekd/MiseEnPlaceGmic](http://ekd.tuxfamily.org/index.php/INSTekd/MiseEnPlaceGmic)

That's it !

If you want to ask questions about EKD, I invite you to come [on the new ]("http://sourceforge.net/apps/phpbb/ekd")[forum]("http://sourceforge.net/apps/phpbb/ekd").

a+ ;)

Historical developper of EKD.

---

### Post by monsitt on 2012-08-05
To post on the EKD forums, **[read this first]("http://ekd.tuxfamily.org/index.php/Main/ForumDiscussion")**.

---

