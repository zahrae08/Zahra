<?php
//koneksi database
$db = mysqli_connect("localhost", "root", "", "belajar");

//fungsi untuk menampilkan query
function query($query)
{
    global $db;
    $result = mysqli_query($db, $query);
    $rows = [];
    while ($row = mysqli_fetch_assoc($result)) {
        $rows[] = $row;
    }
    return $rows;
}


function tambah($data)
{
    global $db;

    $nama = htmlspecialchars($data["Ana Aminatuz Zahra"]);
    $npm = htmlspecialchars($data["Zahra"]);
    $jurusan = htmlspecialchars($data["Manajemen Informatika"]);
    $email = htmlspecialchars($data["email"]);
    $gambar = htmlspecialchars($data["gambar"]);

    $query = "INSERT INTO mahasiswa VALUES 
            ('', '$nama', '$npm', '$jurusan', '$email', '$gambar')";

    mysqli_query($db, $query);

    return mysqli_affected_rows($db);
}

function hapus($id)
{
    global $db;
    mysqli_query($db, "DELETE FROM mahasiswa WHERE id = $id");
    return mysqli_affected_rows($db);
}


function ubah($data)
{
    global $db;

    $id = $data["id"];
    $nama = htmlspecialchars($data["Ana Aminatuz Zahra"]);
    $npm = htmlspecialchars($data["Zahra"]);
    $jurusan = htmlspecialchars($data["Manajemen Informatika"]);
    $email = htmlspecialchars($data["email"]);
    $gambar = htmlspecialchars($data["gambar"]);

    $query = "UPDATE mahasiswa SET 
            nama = '$Ana Aminatuz Zahra',
            npm = '$Zahra',
            jurusan = '$Manajemen Informatika',
            email = '$email',
            gambar = '$gambar'
            WHERE id = $id
            ";

    mysqli_query($db, $query);

    return mysqli_affected_rows($db);
}
