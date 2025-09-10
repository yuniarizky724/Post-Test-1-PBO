# Post-Test-1-PBO
### Rizky Yunia
### Sistem Informasi C
### 2409116089

### Program Butik Penyewaan Busana adalah aplikasi sederhana untuk mengelola daftar busana yang tersedia di sebuah butik penyewaan. Dengan program ini, pengguna dapat menambahkan, melihat, mengubah, dan menghapus data busana, serta keluar dari sistem. Program ini menggunakan ArrayList sebagai tempat penyimpanan data sementara.
### Alur program yaitu: Tampilkan Menu - User pilih menu - Jalankan aksi - kembali ke manu - ulangi sampai keluar.

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */
package Butik_Penyewaan_Busana;
        
import java.util.ArrayList;
import java.util.Scanner;
/**
 *
 * @author user
 */

class Busana {
    String nama;
    double hargaSewa;
    String status;

    public Busana(String nama, double hargaSewa, String status) {
        this.nama = nama;
        this.hargaSewa = hargaSewa;
        this.status = status;
    }

    @Override
    public String toString() {
        return "Nama: " + nama + " | Harga Sewa: Rp" + hargaSewa + " | Status: " + status;
    }
}

public class Butik_Penyewaan_Busana {
    public static void main(String[] args) {
        ArrayList<Busana> daftarBusana = new ArrayList<>();
        try (Scanner input = new Scanner(System.in)) {
            int pilihan;
            
            do {
                System.out.println("\n PENYEWAAN BUSANA");
                System.out.println("1. Tambah Busana");
                System.out.println("2. Lihat Daftar Busana");
                System.out.println("3. Ubah Busana");
                System.out.println("4. Hapus Busana");
                System.out.println("5. Keluar");
                System.out.print("Pilih menu: ");
                
                pilihan = input.nextInt();
                input.nextLine();
                
                switch (pilihan) {
                    case 1 -> {
                        System.out.print("Masukkan nama busana: ");
                        String nama = input.nextLine();
                        System.out.print("Masukkan harga sewa: ");
                        double harga = input.nextDouble();
                        input.nextLine();
                        System.out.print("Masukkan status (Tersedia/Disewa): ");
                        String status = input.nextLine();
                        daftarBusana.add(new Busana(nama, harga, status));
                        System.out.println("Busana berhasil ditambahkan!");
                    }
                    
                    case 2 -> {
                        if (daftarBusana.isEmpty()) {
                            System.out.println("Belum ada busana yang tersedia.");
                        } else {
                            System.out.println("Daftar Busana:");
                            for (int i = 0; i < daftarBusana.size(); i++) {
                                System.out.println((i + 1) + ". " + daftarBusana.get(i));
                            }
                        }
                    }
                    
                    case 3 -> {
                        if (daftarBusana.isEmpty()) {
                            System.out.println("Belum ada busana yang tersedia.");
                        } else {
                            System.out.println("Pilih nomor busana yang ingin diubah:");
                            for (int i = 0; i < daftarBusana.size(); i++) {
                                System.out.println((i + 1) + ". " + daftarBusana.get(i));
                            }
                            System.out.print("Masukkan nomor: ");
                            int indexUbah = input.nextInt();
                            input.nextLine();
                            if (indexUbah > 0 && indexUbah <= daftarBusana.size()) {
                                System.out.print("Masukkan nama busana baru: ");
                                String nama = input.nextLine();
                                System.out.print("Masukkan harga sewa baru: ");
                                double harga = input.nextDouble();
                                input.nextLine();
                                System.out.print("Masukkan status baru: ");
                                String status = input.nextLine();
                                daftarBusana.set(indexUbah - 1, new Busana(nama, harga, status));
                                System.out.println("Busana berhasil diubah!");
                            } else {
                                System.out.println("Nomor tidak valid!");
                            }
                        }
                    }
                    
                    case 4 -> {
                        // Delete
                        if (daftarBusana.isEmpty()) {
                            System.out.println("Belum ada busana yang tersedia.");
                        } else {
                            System.out.println("Pilih nomor busana yang ingin dihapus:");
                            for (int i = 0; i < daftarBusana.size(); i++) {
                                System.out.println((i + 1) + ". " + daftarBusana.get(i));
                            }
                            System.out.print("Masukkan nomor: ");
                            int indexHapus = input.nextInt();
                            input.nextLine();
                            if (indexHapus > 0 && indexHapus <= daftarBusana.size()) {
                                daftarBusana.remove(indexHapus - 1);
                                System.out.println("Busana berhasil dihapus!");
                            } else {
                                System.out.println("Nomor tidak valid!");
                            }
                        }
                    }
                    
                    case 5 -> System.out.println("Terima kasih!");
                    
                    default -> System.out.println("Pilihan tidak valid.");
                }
                
            } while (pilihan != 5);
        }
    }
}
