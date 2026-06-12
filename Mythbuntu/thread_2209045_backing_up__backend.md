---
title: "backing up  backend"
date: 2014-03-03
forum: Mythbuntu
---

### Post by benlyboy on 2014-03-03
Hi i'm hoping someone can help.
i'm trying to back up my mythbuntu 10.10 system so i can nove it over to a new system. but when i run mythconverg_backup.pl it seems at first to work but the file that is created seems to be empty insted of the file ending with .gz as i have seen before, it ends with .sql, and seems to be a single page file that can be opend in gedit. 

this is the full content of that file

> -- MySQL dump 10.13  Distrib 5.1.49, for debian-linux-gnu (x86_64)
--
-- Host: localhost    Database: mythconverg
-- ------------------------------------------------------
-- Server version	5.1.49-1ubuntu8.1

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

If anyone has any ideas i would be greatful thanks

---

### Post by khPWXxF on 2014-03-03
Any clues if you try to  backup with the --verbose parameter?

Phil

---

### Post by benlyboy on 2014-03-06
Thanks Phil
Been a busy week but will give that a go on the weekend and will post the results

---

