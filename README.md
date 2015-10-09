# Kisuu.java
基数変換
import java.util.Scanner; // スキャナクラスのインポート宣言

class Kisuu {

	static int cardConvR(int x, int r, char[] d) { // 基数変換
		int digits = 0; // 変換後の桁数
		String dchar = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
		
		do {
			d[digits++] = dchar.charAt(x%r);
			// rで割った剰余を文字列にして格納，後置インクリメントに注意
			x /= r;
		} while (x != 0); // 零になったら終了，非零の間繰り返す
		return digits; // 変換後の桁数を返す
	}
	
	public static void main(String[] args) { // メイン関数
		Scanner stdIn = new Scanner(System.in);
		// スキャナークラスのインスタンス生成，System.inは標準入出力ストリーム
		int n; // 変換対象の整数
		int d; // 基数
		int m; // 変換結果の桁数
		int retry; // 繰り返し確認
		char[] r = new char[32]; // 変換後の各桁を格納する配列
		
		System.out.println("10進数を基数変換します．");
		do {
			do { // 変換対象の読み込み
				System.out.print("変換する非負の整数：");
				n = stdIn.nextInt();
			} while (n<0);
			
			do {
				System.out.print("何進数に変換しますか（2,8,16）：");
				d = stdIn.nextInt();
			} while (d!=2&&d!=8&&d!=16);
			
			m = cardConvR(n,d,r); // 基数変換
			
			System.out.print(d + "進数では");
			for (int i=m‐1;i>=0;i‐‐) // 上位桁から順に表示
				System.out.print(r[i]);
			System.out.println("です．");
			
			System.out.print("もう一度しますか（1：はい 0：いいえ）：");
			retry = stdIn.nextInt();
		} while (retry == 1);
	}
}
