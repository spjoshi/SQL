## Import/Export database using dump

#### Export db  
C:\Users\Me>pg_dump -U postgres -h localhost hs611db_win > dumpMedicare.sql  

#### Create a new db to import the above file  
create database newmedicare;  
CREATE DATABASE  

#### Import the above sql file into the new db
C:\Users\Me>psql -d newmedicare -f dumpMedicare.sql

#### Check if data is present
select (*) from cmspop;  
count  
--------  
2255098  
(1 row)  

### Select top 5 rows  
select * from cmspop limit 5;

### Import database using copy 
##### Create tables

CREATE TABLE cmspop (  
id char(16),  
dob char(10),  
dod char(10),  
sex varchar(6),  
race varchar(8),  
state varchar(4),  
county smallint,  
alz_rel_sen boolean,  
heart_fail boolean,  
cancer boolean,  
depression boolean  
);  
CREATE TABLE cmsclaims (  
id char(16),  
hmo_mo smallint,  
carrier_reimb int,  
bene_resp int  
);  
#### Download two csv files into Downloads folder
#### Copy the data into the tables
COPY cmspop FROM C:\Users\Me\Downloads\medicare_2010_pop_data.csv' DELIMITER ',' HEADER CSV;   
	  
COPY cmsclaims FROM 'C:\Users\Me\Downloads\medicare_2010_payer_data.csv' DELIMITER ',' HEADER CSV;

## Create a new user
C:\Users\Me>createuser -U postgres -P -s -e newuser1  
Enter password for new role:  
Enter it again:  
CREATE ROLE 'newuser1' PASSWORD 'md5lakdjfadf9a8df09asdf70asd8f0a9sdf' SUPERUSER CREATEDB  
CREATEROLE INHERIT LOGIN;  

## Useful commands  
\l --> list databases  
\c --> change database  
\dt --> list tables  
\du --> list users and their previledges  
