create database if not exists socialmediaapplication; 

use socialmediaapplication;
drop table if exists CommentTable;
drop table if exists PostTable;
drop table if exists UserTable;

create table UserTable (
	UsernameID varchar(20) not null UNIQUE,
	Password varchar(20) not null,
	Email varchar (255),
	primary key (UsernameID)

);

create table PostTable (
	PostID int(7) not null auto_increment,
	UsernameID varchar (20) not null UNIQUE, 
	PostString varchar(1000) not null,
	PostDate datetime default current_timestamp,
	primary key (PostID),
	foreign key (UsernameID) references UserTable(UsernameID)
	

);

create table CommentTable (
	CommentID int(7) not null auto_increment,
	PostID int(7) not null,
	UsernameID varchar (20) not null UNIQUE, 
	CommentString varchar(1000) not null,
	CommentDate datetime default current_timestamp,
	primary key (CommentID),
	foreign key (PostID) references PostTable(PostID),
	foreign key (UsernameID) references UserTable(UsernameID)

);